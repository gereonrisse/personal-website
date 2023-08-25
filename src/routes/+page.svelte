<script>
    import SocialIcon from "$lib/SocialIcon.svelte";
    import GitHub from "$lib/svg/GitHub.svelte";
    import LinkedIn from "$lib/svg/LinkedIn.svelte";
    import ResumeCard from "$lib/ResumeCard.svelte";
    import Tag from "$lib/Tag.svelte";
    import Link from "$lib/ExternalLink.svelte";
</script>

<svelte:head>
    <title>Gereon Risse</title>
    <meta content="Personal website of Gereon Risse" name="description"/>
</svelte:head>

<!-- INTRO SECTION -->
<section class="flex flex-col sm:flex-row gap-6 sm:gap-12 mt-16">

    <!-- Header & Socials -->
    <div class="sm:basis-1/3 flex flex-col">
		<h1 class="text-4xl font-bold text-slate-100">
            Hello, I'm Gereon
        </h1>
		<h2 class="text-xl font-bold text-slate-500 mt-6">
            Sound engineer<br>Software engineer<br>Musician
        </h2>
        <div class="mt-auto flex flex-row gap-4">
            <SocialIcon>
                <GitHub/>
            </SocialIcon>
            <SocialIcon>
                <LinkedIn/>
            </SocialIcon>
        </div>
	</div>

    <!-- Text -->
    <div class="sm:basis-2/3 leading-relaxed flex flex-col gap-2 text-slate-300">
        <p>
            Since my early days, I've been immersed in the realm of sound – from doing technical studio work like mixing
            and mastering, working as a live sound engineer, and composing my own music.
        </p>
        <p>
            Five years ago, I ventured into the realm of software engineering, diving deep into data engineering, web
            app development, and eventually taking on project leadership roles.
        </p>
        <p>
            My passion for both sound and code converged when I embarked on a project in late 2022 – crafting a Digital
            Signal Processor (DSP), a sophisticated sonic computer that takes speaker systems to a new level.
        </p>
    </div>
</section>

<!-- SOFTWARE SECTION -->
<section class="flex flex-col gap-8">
    <ResumeCard>
        <span slot="timespan">
            since 2022
        </span>
        <span slot="header">
            DSP Prototype development
        </span>
        <span slot="description">
            Created a real-time audio processing engine in Rust, which is controlled by a node-based web application.
            Built a Raspberry Pi based hardware prototype.
        </span>
        <span slot="tags" class="flex flex-row gap-2">
            <Tag>Rust</Tag>
            <Tag>TypeScript</Tag>
            <Tag>SvelteKit</Tag>
        </span>
    </ResumeCard>

    <ResumeCard>
        <span slot="timespan">
            2021 - 2022
        </span>
        <span slot="header">
            Lead Engineer & Project Manager
        </span>
        <span slot="company">
            <Link href="https://digital-services.team/">
                digital-services.team GmbH
            </Link>
        </span>
        <span slot="description">
            Created a web application for building and optimizing websites.
            Led a team of engineers, specified software architecture, designed UI and UX.
        </span>
        <span slot="tags" class="flex flex-row gap-2">
            <Tag>PHP</Tag>
            <Tag>Laravel</Tag>
            <Tag>Vue 3</Tag>
        </span>
    </ResumeCard>

    <ResumeCard>
        <span slot="timespan">
            2018 - 2021
        </span>
        <span slot="header">
            Software & Data Engineer
        </span>
        <span slot="company">
            <Link href="https://www.integrated-analytics.de/">
                Integrated Analytics GmbH
            </Link>
        </span>
        <span slot="description">
            Designed and implemented data pipelines for large-scale data warehousing and analytics projects.
            Created web applications utilized within the company and for external clients.
        </span>
        <span slot="tags" class="flex flex-row gap-2">
            <Tag>MySQL</Tag>
            <Tag>PHP</Tag>
            <Tag>Laravel</Tag>
            <Tag>HTML</Tag>
            <Tag>CSS</Tag>
            <Tag>JavaScript</Tag>
        </span>
    </ResumeCard>
</section>
