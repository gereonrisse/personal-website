<script>
    import SvelteMarkdown from 'svelte-markdown'

    const source = `
TODO TLDR

# The Idea
I love music, especially on the electronic side of things. And I love the sound systems that reproduce this music.
So naturally, for the events I work at and for the parties my friends and me organize, it occured to me that I need an Audio DSP in my arsenal to tune the speaker systems to my liking.
For those who don't know: An Audio DSP (Digital Signal Processor) is basically a computer that is highly specialized in applying sound shaping algorithms to a signal.
You can put it between a source (your phone, the DJ Mixer, etc.) and your speaker system.
The signal can then be shaped specifically to compensate errors in a loudspeaker and match different sound speakers together to form a coherent system.

So, in summer of 2022, I bought a powerful DSP, a dbx VENU360, and built a 19" rack for it while patiently awaiting shipment.
But then the chip crisis destroyed my plans: I got a mail that the DSP would not be shipped this year; in fact, it is still not available to this day.

At the same time, I started learning about the underlying technology of DSPs, and quickly came to know that they use specialized CPUs that can do signal processing very well, but nothing else particularly good.
Most have implemented a fixed processing chain, which makes them very reliable, but at the same time very limited.
The user can change parameters, but if you were to change the processing order or add an additional step, you're out of luck.
Some DSPs are more flexible in that regard, but then you often have to compile your processing chain to machine code and upload it to the hardware.
Not very convenient when you're working at a concert under high time constraints.

These constraints made perfect sense when DSPs were first used in speaker systems in the last century. But compared to that, nowadays we have virtually unlimited processing power in our computers.
Also, with more processing power, more advanced sound shaping algorithms can be employed.

Using a DAW (a software for music production and processing), you can easily route your audio into an ordinary computer, and apply any fancy processing chain you'd like live and in real-time.
I actually did that in my living room using a 10 year old iMac, and it works flawlessly.
I still wouldn't use that kind of setup in a live venue, because the used soft- and hardware are not made for that purpose.
Therefore the setup is somewhat inconvenient to use and doesn't give you any guarantees about reliability.

So yeah, I'm a software developer and I want a powerful DSP. The challenge is on!

# The Goals & Tech Stack
It is not realistic to create a full-blown production-ready product like this alone and in a timely manner, so the goal is to create a minimal prototype.

I decided to make the processing chain node-based: Each processing step is a node, you can add as many as you like and connect them freely.

One of the defining challenges of this project is that it needs to be real-time: In a typical application, the DSP has 0.8ms to process the current signal.
If it were to take any longer even once, the only thing you'd hear are ugly loud clicking noises.
To guarantee this, a real-time patched Linux needs to be used: It grants the software any processing power it needs right away, disregarding anything else that runs on the computer.
For the same reason, you need to write the code in a programming language that provides low-level control over the machine; I therefore decided to settle on Rust.

The machine can then be attached to a network (Ethernet cable of Wi-Fi), or alternatively host its own.
It hosts a webserver providing the control interface, which means you can control the engine by simply opening a website on your laptop or phone.
No more installing of horrendously outdated control programs that only run on Windows XP, yay!

I use a Raspberry Pi as the hardware foundation, because for now it is easy to work with. In the future, more specialized hardware can be used.
Attached to it is a Behringer UMC1820, which provides audio inputs/outputs and conversion from analog to digital and vice versa.
You couldn't use that in a real production system, since it adds a lot of latency (~30ms).
This could be mitigated by building a custom sound interface that connects directly to the GPIO pins of the Pi, but I'm not an electrical engineer, so the Behringer must suffice for now.
TODO Hardware photo

# Implementing & The Point of Failure
So I got started on implementing. I started with the engine, and along the way I learned a lot about Rust, real-time programming, graph algorithms, concurrency and much more.
After a few months, I got a working engine. Since there was no frontend yet, the only way to control it was by either changing savefiles or an interactive CLI.
As a demonstration, I created a signal chain for my desk speakers and it actually worked. Huge success!
TODO CLI screenshot, processing chain drawing

While implementing, the biggest challenge for me was concurrency: How could you alter the processing chain from the outside while the engine is continuously working on it?
There are sophisticated (and really complex!) paradigms for this problem, but this was my first time doing low-level programming outside of university, and I couldn't quite wrap my head around them at the time.
So I chose the naive approach of using mutexes for the time.
Basically, mutexes just ensure that only one part of the program at a time accesses the processing chain by making all other parts wait until it is free again.
This of course stands against the real-time principle: The engine isn't supposed to wait on another thread writing its changes, because it must finish its processing within those 0.8ms.
But as long as there are not a lot of changes, it worked and I could continue tackling other challenges.

I then started implementing the frontend: A webpage, hosted by the engine itself, where you can drag around and connect the nodes to your liking.
I used SvelteKit as a framework, which made it easy for me to turn ordinary HTML markup into a highly interactive app that feels more like a video game than a web page.
TODO frontend gif

After a few weeks, many aspects of the processing chain could be controlled live in a user-friendly manner.
I then tackled the challenge of visualization: Live dB meters that show you the current amplitude, frequency graph etc.
TODO db meter gif

As you can see, I got that to work as well, but here the problems started to arise:
In order to visualize with 60 FPS, you'd have to access the processing chain 60 times a second.
Remember my naive mutex implementation? Yeah, that's where it came back on me. Suddenly, the engine started to have a lot of outages.
Additionally, since I didn't know much about organizing data structures in concurrent programs properly, race conditions started to surface which crashed the engine entirely.

At that point, it became clear to me that the codebase of the engine was deeply faulted and continuation of the development became unfeasible.
After all, I just learned the language while coding in it, and also had to learn so many low-level paradigms on the way.
As a result, the codebase is horrible, and know I know how to do it properly.

# What's next
So yeah, the time to start over has come. I will rewrite the codebase from ground up, and this time with a proper architecture in mind from the start.
It's a bit sad that the old engine has to go, but I don't feel the eight months I spent on the project are lost at all.
It was a huge learning experience that increased my low-level skills drastically.

I will try to manifest future developments in more blog posts, which will probably be much more technical than this one.

Thanks for reading!

    `

</script>

<SvelteMarkdown {source} />