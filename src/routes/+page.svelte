<script>
    import ResumeCard from "$lib/ResumeCard.svelte";
    import Tag from "$lib/Tag.svelte";
    import Link from "$lib/ExternalLink.svelte";
    import { t } from '$lib/translations';
    import SectionHeader from "$lib/SectionHeader.svelte";
    import Button from "$lib/Button.svelte";
    import Divider from "$lib/Divider.svelte";
    import DownArrow from "$lib/svg/DownArrow.svelte";
    import { browser } from '$app/environment';
    import { fade } from 'svelte/transition';

    // Down Arrow.
    let showArrow = true;
    if (browser) {
        const handleScroll = () => {
            showArrow = false;
            window.removeEventListener('scroll', handleScroll);
        };
        window.addEventListener('scroll', handleScroll);
    }
</script>

<svelte:head>
    <title>Gereon Risse</title>
    <meta content="Personal website of Gereon Risse" name="description"/>
</svelte:head>

<!-- INTRO SECTION -->
<section class="flex flex-col min-h-screen my-auto justify-center max-w-5xl">
    <div class="flex flex-col sm:flex-row gap-6 sm:gap-12 px-4">
        <!-- Header -->
        <div class="sm:basis-1/3 flex flex-col">
            <h1 class="text-4xl font-bold text-slate-100 animate-fade-in motion-reduce:animate-none">
                {$t('home.title')}
            </h1>
            <nav class="text-xl font-bold text-slate-500 my-6 leading-relaxed animate-fly-in-fast motion-reduce:animate-none">
                <ol>
                    <li class="hover:text-rose-300"><a href="#software">{$t('home.subtitle1')}</a></li>
                    <li class="hover:text-rose-300"><a href="#audio">{$t('home.subtitle2')}</a></li>
                    <li class="hover:text-rose-300"><a href="#music">{$t('home.subtitle3')}</a></li>
                </ol>
            </nav>
        </div>

        <!-- Text -->
        <div class="sm:basis-2/3 leading-relaxed flex flex-col gap-2 text-slate-300 animate-fly-in-slow motion-reduce:animate-none">
            <p>{$t('home.intro.p1')}</p>
            <p>{$t('home.intro.p2')}</p>
            <p>{$t('home.intro.p3')}</p>
        </div>
    </div>
</section>

<!-- Down Arrow -->
{#if showArrow}
    <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 mb-8 h-6 w-6 text-slate-300 animate-fade-in-delayed motion-reduce:animate-none" transition:fade>
        <DownArrow />
    </div>
{/if}

<div class="flex flex-col gap-12 sm:gap-32">
    <Divider />

    <!-- SOFTWARE SECTION -->
    <section>
        <SectionHeader name="software">{$t('home.software.header')}</SectionHeader>

        <!-- Resume cards -->
        <div class="mt-12 flex flex-col gap-8">
            <!-- DSP -->
            <ResumeCard>
                <span slot="timespan">
                    {$t('home.software.dsp.timespan')}
                </span>
                        <span slot="header">
                    {$t('home.software.dsp.header')}
                </span>
                        <span slot="description">
                    {$t('home.software.dsp.description')}
                </span>
                        <span slot="tags" class="flex flex-row flex-wrap gap-2">
                    <Tag>Rust</Tag>
                    <Tag>TypeScript</Tag>
                    <Tag>SvelteKit</Tag>
                </span>
            </ResumeCard>

            <!-- digital-services -->
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
                    {$t('home.software.digital-services.description')}
                </span>
                        <span slot="tags" class="flex flex-row flex-wrap gap-2">
                    <Tag>PHP</Tag>
                    <Tag>Laravel</Tag>
                    <Tag>Vue 3</Tag>
                    <Tag>Figma</Tag>
                </span>
            </ResumeCard>

            <!-- Integrated Analytics -->
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
                    {$t('home.software.integrated-analytics.description')}
                </span>
                        <span slot="tags" class="flex flex-row flex-wrap gap-2">
                    <Tag>MySQL</Tag>
                    <Tag>PHP</Tag>
                    <Tag>Laravel</Tag>
                    <Tag>HTML</Tag>
                    <Tag>CSS</Tag>
                    <Tag>JavaScript</Tag>
                </span>
            </ResumeCard>

            <!-- University -->
            <ResumeCard>
                <span slot="timespan">
                    since 2018
                </span>
                        <span slot="header">
                    Computer Science Student
                </span>
                        <span slot="company">
                    <Link href="https://www.uni-bonn.de/en">
                        University of Bonn
                    </Link>
                </span>
                        <span slot="description">
                    {$t('home.software.university.description')}
                </span>
            </ResumeCard>

            <!-- TODO add CV -->
            <!-- <div>
                <div class="mx-auto max-w-sm">
                    <Button>
                        <a href="#" target="_blank">{$t('home.software.cv')}</a>
                    </Button>
                </div>
            </div> -->

        </div>
    </section>

    <Divider />

    <!-- AUDIO ENGINEER SECTION -->
    <section>
        <SectionHeader name="audio">{$t('home.audio.header')}</SectionHeader>

        <div class="px-4 mt-6 sm:mt-8 mx-auto max-w-md">
            <div class="leading-relaxed text-slate-300">
                <p>{$t('home.audio.text')}</p>

                <ul class="mt-4 ml-6 text-slate-300 list-disc">
                    <li>{$t('home.audio.bullet1')}</li>
                    <li>{$t('home.audio.bullet2')}</li>
                    <li>{$t('home.audio.bullet3')}</li>
                </ul>
            </div>

            <div class="mt-6 sm:mt-8 text-center">
                <Button>
                    <a href="mailto:gereon.risse@gmail.com">{$t('home.audio.button')}</a>
                </Button>
            </div>
        </div>
    </section>

    <Divider />

    <!-- MUSIC SECTION -->
    <section>
        <SectionHeader name="music">{$t('home.music.header')}</SectionHeader>

        <div class="px-4 mt-6 sm:mt-8 mx-auto max-w-md text-center">
            <p class="leading-relaxed text-slate-300">{$t('home.music.text')}</p>

            <div class="mt-6 sm:mt-8 w-full text-center">
                <Button>
                    <a href="https://gereon.online/" target="_blank">{$t('home.music.button')}</a>
                </Button>
            </div>
        </div>
    </section>
</div>