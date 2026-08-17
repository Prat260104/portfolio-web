<template>
  <section id="works" class="common-padding mb-20">
    <div class="flex flex-col">
      <h3
        id="selectedWorks"
        v-html="selectedWorks"
        class="heading-1 text-start leading-none font-bold uppercase"
      ></h3>
      <p
        class="heading-1 text-flax-smoke-400 text-opacity-50 hidden w-4/5 text-end font-extrabold sm:block"
      >
        ( {{ selectedWorksProps.length }} )
      </p>

      <div
        id="selected-works-text"
        class="md:column-gap text-flax-smoke-300 mt-[5%] grid grid-cols-12 justify-end opacity-0 lg:grid"
      >
        <p
          class="heading-6 text-flax-smoke-300/85 col-span-4 text-center text-nowrap lg:col-start-2"
        >
          (
          <span class="inline sm:hidden">{{ selectedWorksProps.length }} </span>
          PROJECTS )
        </p>
        <p
          class="heading-4 font-fancy col-span-8 w-full text-balance sm:font-semibold lg:col-span-7"
        >
          A curated showcase of client solutions, university tech-club platforms,
          and self-driven engineering projects meticulously crafted with clean UI/UX and purpose.
        </p>
      </div>
    </div>

    <div
      class="sm:column-gap relative mt-12 grid size-full grid-cols-12 lg:mt-[10%]"
    >
      <div
        class="sticky top-16 col-span-5 hidden h-fit w-full flex-col pr-6 lg:pr-12 md:flex select-none"
      >
        <div
          class="text-flax-smoke-100 flex w-full overflow-hidden text-[11vw] lg:text-[12.5vw] leading-[0.85] font-semibold"
        >
          <span class="font-title! relative -tracking-wider">0</span>
          <span
            id="index"
            class="font-title! relative -tracking-wider will-change-transform"
            >{{ index + 1 }}.</span
          >
        </div>

        <div
          id="project-info"
          class="mt-4 flex flex-col gap-4 overflow-hidden will-change-transform"
        >
          <div>
            <div class="flex items-center gap-2">
              <span class="rounded-full border border-flax-smoke-700 bg-flax-smoke-900/60 px-3 py-0.5 text-xs font-mono uppercase tracking-wider text-flax-smoke-300">
                {{ selectedWorksProps[index].category }}
              </span>
              <span class="rounded-full border border-flax-smoke-800 px-2.5 py-0.5 text-xs font-mono text-flax-smoke-400">
                {{ selectedWorksProps[index].year }}
              </span>
            </div>

            <h3 class="heading-4 lg:heading-3 font-title! mt-2.5 font-bold uppercase tracking-tight text-flax-smoke-100">
              {{ selectedWorksProps[index].name }}
            </h3>
          </div>

          <p class="text-base font-medium leading-snug text-flax-smoke-200 lg:text-lg">
            {{ selectedWorksProps[index].description }}
          </p>

          <div class="rounded-xl border border-flax-smoke-800/80 bg-flax-smoke-950/50 p-4 backdrop-blur-xs lg:p-5">
            <div class="mb-2 flex items-center gap-2">
              <span class="size-1.5 rounded-full bg-[#34A853]"></span>
              <span class="font-mono text-xs font-semibold tracking-wider uppercase text-flax-smoke-300">
                UX Strategy & Rationale
              </span>
            </div>
            <p class="text-xs leading-relaxed text-flax-smoke-300/90 lg:text-sm font-normal">
              {{ selectedWorksProps[index].rationale }}
            </p>
          </div>

          <a
            :href="selectedWorksProps[index].url"
            target="_blank"
            class="group inline-flex w-fit items-center gap-2 font-mono text-xs font-semibold tracking-widest uppercase text-flax-smoke-300 transition-colors hover:text-flax-smoke-100"
          >
            <span class="border-b border-flax-smoke-600 pb-0.5 transition-colors group-hover:border-flax-smoke-200">
              Launch Live Product
            </span>
            <span class="transition-transform duration-300 group-hover:translate-x-1 group-hover:-translate-y-0.5">↗</span>
          </a>
        </div>
      </div>
      <aside
        @mouseenter="showCursor"
        @mouseleave="hideCursor"
        class="relative col-span-full flex flex-col space-y-10 md:col-span-7"
      >
        <div
          v-for="(work, i) in selectedWorksProps"
          :key="i"
          class="work-card @container"
        >
          <a class="group" target="_blank" :href="work.url">
            <div
              class="flex-center relative aspect-square overflow-clip rounded-lg"
            >
              <img
                alt="work-background"
                loading="lazy"
                class="absolute size-full object-cover select-none"
                :src="work.imageBg"
              />
              <div
                class="flex-center z-10 aspect-4/3 size-full overflow-clip rounded-lg object-cover"
              >
                <img
                  :src="work.imageSrc"
                  alt="work-preview"
                  class="max-h-[85%] max-w-[90%] rounded-md object-contain shadow-2xl transition-transform duration-500 ease-in-out group-hover:scale-105"
                />
              </div>
            </div>
            <div>
              <p class="heading-6 font-title! mt-[2%] mb-[1%] leading-none">
                {{ work.category }}
              </p>
              <div class="items-center justify-between sm:flex">
                <h3 class="heading-3 font-title! font-bold uppercase">
                  {{ work.name }}
                </h3>
                <div class="flex gap-1.5 select-none">
                  <p
                    class="border-flax-smoke-300 hover:bg-flax-smoke-300 hover:text-flax-smoke-900 rounded-full border px-4 py-2 transition-[background-color,color] duration-500 ease-in-out"
                    v-for="tag in work.tags"
                    :key="tag"
                  >
                    <span>{{ tag }}</span>
                  </p>
                  <p
                    class="border-flax-smoke-300 bg-flax-smoke-300 text-flax-smoke-900 hover:text-flax-smoke-300 rounded-full border px-4 py-2 transition-[background-color,color] duration-500 ease-in-out hover:bg-transparent"
                  >
                    <span>{{ work.year }}</span>
                  </p>
                </div>
              </div>
            </div>
          </a>
        </div>
      </aside>
    </div>
  </section>
</template>

<script setup lang="ts">
  import { animateSplitText } from '@/animations';
  import { textSplitterIntoChar } from '@/functions';
  import { computed, onBeforeMount, onMounted, ref } from 'vue';
  import gsap from 'gsap';
  import { useWindowSize } from '@vueuse/core';
  import {
    project_kiet,
    project_nextgen,
    project_noteboat,
    project_hostelwallah,
    workBg1,
    workBg2,
    workBg3,
    workBg4,
  } from '@/assets/images';

  const isSmallScreen = computed(() => {
    return useWindowSize().width.value < 768;
  });
  const index = ref(0);
  const selectedWorks = ref('Selected Projects /');

  const tl = gsap
    .timeline({ defaults: { duration: 0.25 } })
    .to(['#cursor', '#inner'], {
      scale: 1,
      opacity: 1,
    })
    .paused(true);

  const showCursor = () => {
    tl.play();
  };
  const hideCursor = () => {
    tl.reverse();
  };

  const selectedWorksProps = [
    {
      name: 'KIET CSE-AIML Portal',
      category: 'UI/UX & Web Development',
      tags: ['UI/UX Design', 'Institutional', 'Web Portal'],
      description:
        'Architected an intuitive institutional web portal with structured academic curricula, interactive faculty directories, and departmental achievements.',
      rationale:
        'Standard university portals are text-heavy and fragmented. Adopted an open-grid layout with high typographic contrast and streamlined navigation, enabling users to access key syllabus, facilities, and faculties within 2 clicks.',
      imageSrc: project_kiet,
      imageBg: workBg1,
      url: 'https://www.kiet.edu/programs/b-tech/cse-aiml/',
      year: '2025',
    },
    {
      name: 'NextGen Supercomputing',
      category: 'UI/UX & Web Platform',
      tags: ['UI/UX Design', '3D & AI', 'Supercomputing Club'],
      description:
        'Crafted a high-performance interactive web presence showcasing our club’s in-house RIVA machine learning model with 3D generative visuals and dark aesthetic storytelling.',
      rationale:
        'Our club operates an on-premise NVIDIA DGX A100 supercomputer. I intentionally crafted the design system around deep obsidian blacks and electric green accents paying homage to NVIDIA’s visual identity, creating an authentic high-compute atmosphere for AI and student research.',
      imageSrc: project_nextgen,
      imageBg: workBg2,
      url: 'https://www.nextgen-supercomputing.in/',
      year: '2025',
    },
    {
      name: 'Noteboat',
      category: 'SaaS & Resource Platform',
      tags: ['UI/UX Design', 'Dashboard', 'Centralized Hub'],
      description:
        'Designed a centralized academic knowledge dashboard with multi-branch subject filters and organized student resource directories.',
      rationale:
        'Engineering students struggle with scattered study materials. Implemented an organized dark-mode sidebar layout with collapsible directories and branch filters to minimize cognitive overload.',
      imageSrc: project_noteboat,
      imageBg: workBg3,
      url: 'https://www.noteboat.store/',
      year: '2025',
    },
    {
      name: 'Hostel Wallah',
      category: 'Full-Stack & Marketplace',
      tags: ['UI/UX Design', 'Marketplace', 'Full-Stack'],
      description:
        'Engineered an end-to-end student accommodation marketplace featuring multi-attribute property filters, transparent pricing cards, and direct booking flows.',
      rationale:
        'Student housing platforms often lack clarity. Designed high-density accommodation cards with verified amenity pills and zero-brokerage badges to establish immediate renter trust.',
      imageSrc: project_hostelwallah,
      imageBg: workBg4,
      url: 'https://hostelwallah.com/',
      year: '2025',
    },
  ];

  // Reusable function to handle forward scroll animation
  const createForwardTimeline = (
    index: any,
    i: any,
    selectedWorksProps: any[],
  ) => {
    const tl = gsap.timeline({
      defaults: { duration: 0.3 },
    });

    tl.to('#project-info', {
      opacity: 0,
      y: -15,
      duration: 0.18,
      ease: 'power1.in',
    })
      .set('#index', {
        yPercent: 100,
        onComplete: () => {
          index.value = Math.min(i, selectedWorksProps.length - 1);
        },
      })
      .to('#index', {
        yPercent: 0,
        ease: 'power1.inOut',
      })
      .fromTo(
        '#project-info',
        { opacity: 0, y: 15 },
        { opacity: 1, y: 0, duration: 0.28, ease: 'power1.out' },
        '<0.05',
      );

    return tl;
  };

  // Reusable function to handle backward scroll animation
  const createBackwardTimeline = (index: any, i: any) => {
    const tl = gsap.timeline({ defaults: { duration: 0.3 } });

    tl.to('#project-info', {
      opacity: 0,
      y: 15,
      duration: 0.18,
      ease: 'power1.in',
    })
      .set('#index', {
        yPercent: -100,
        onComplete: () => {
          index.value = Math.max(i, 0);
        },
      })
      .to('#index', {
        yPercent: 0,
        duration: 0.3,
        ease: 'power1.inOut',
      })
      .fromTo(
        '#project-info',
        { opacity: 0, y: -15 },
        { opacity: 1, y: 0, duration: 0.28, ease: 'power1.out' },
        '<0.05',
      );

    return tl;
  };

  onBeforeMount(() => {
    selectedWorks.value = textSplitterIntoChar('Selected Works / ', true);
  });

  onMounted(() => {
    animateSplitText(
      '#selectedWorks .letters',
      '#selected-works-text',
      0.7,
      0.01,
      0,
    );

    // Apply GSAP animations to each div
    if (!isSmallScreen.value)
      gsap.utils.toArray('.work-card').forEach((div: any, i: any) => {
        gsap.timeline({ defaults: { duration: 0.7 } }).to(div, {
          scrollTrigger: {
            trigger: div,
            // start: 'top 40%',
            start: 'top 25%',
            // end: 'bottom 40%',
            end: 'bottom 25%',
            scrub: 0.01,
            // markers: true,
            onLeaveBack: () => {
              // Backward scroll animation
              if (index.value !== 0) {
                gsap.to('#index', {
                  yPercent: 100,
                  duration: 0.3,
                  ease: 'power4.inOut',
                  onComplete: () => {
                    createBackwardTimeline(index, i - 1);
                  },
                });
              }
            },
          },
          ease: 'power1.inOut',
          onComplete: () => {
            // Forward scroll animation
            if (index.value !== selectedWorksProps.length - 1) {
              gsap.to('#index', {
                yPercent: -100,
                duration: 0.3,
                ease: 'power4.inOut',
                onComplete: () => {
                  createForwardTimeline(index, i + 1, selectedWorksProps);
                },
              });
            }
          },
        });
      });
  });
</script>
