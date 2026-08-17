<template>
  <section
    id="marquee-section"
    class="text-flax-smoke-200 relative my-24 w-full overflow-hidden leading-none select-none"
  >
    <!-- Row 1 (Moves Left) -->
    <div class="marquee-track flex whitespace-nowrap py-3">
      <div class="marquee-content flex items-center shrink-0">
        <template v-for="item in itemsRow1" :key="item">
          <span
            class="sm:heading-1 mx-6 flex items-center text-3xl font-bold uppercase tracking-tight md:mx-10"
          >
            {{ item }}
            <svg
              class="ml-6 mr-2 inline-block size-6 sm:size-10 text-flax-smoke-400/60"
              viewBox="0 0 100 101"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M49.8234 1.99099C49.4293 9.09696 46.8886 17.4122 43.0707 24.0426C35.0272 38.01 21.1141 47.4665 5.21739 49.7899C4.1712 49.9394 2.55435 50.1024 1.65761 50.1567C0.747283 50.1975 0 50.279 0 50.3334C0 50.3877 0.747283 50.4692 1.65761 50.51C2.55435 50.5644 4.1712 50.7274 5.21739 50.8769C21.1141 53.2002 35.0272 62.6567 43.0707 76.6241C46.8886 83.2546 49.4293 91.5698 49.8234 98.6758C49.8641 99.5861 49.9457 100.333 50 100.333C50.0543 100.333 50.1359 99.5861 50.1766 98.6758C50.5707 91.5698 53.1114 83.2546 56.9293 76.6241C64.9728 62.6567 78.8859 53.2002 94.7826 50.8769C95.8288 50.7274 97.4456 50.5644 98.3424 50.51C99.2527 50.4692 100 50.3877 100 50.3334C100 50.279 99.2527 50.1975 98.3424 50.1567C97.4456 50.1024 95.8288 49.9394 94.7826 49.7899C78.8859 47.4665 64.9728 38.01 56.9293 24.0426C53.1114 17.4122 50.5707 9.09696 50.1766 1.99099C50.1359 1.08066 50.0543 0.333377 50 0.333377C49.9457 0.333377 49.8641 1.08066 49.8234 1.99099Z"
                class="fill-current"
              />
            </svg>
          </span>
        </template>
      </div>
      <div class="marquee-content flex items-center shrink-0" aria-hidden="true">
        <template v-for="item in itemsRow1" :key="item + '-clone'">
          <span
            class="sm:heading-1 mx-6 flex items-center text-3xl font-bold uppercase tracking-tight md:mx-10"
          >
            {{ item }}
            <svg
              class="ml-6 mr-2 inline-block size-6 sm:size-10 text-flax-smoke-400/60"
              viewBox="0 0 100 101"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M49.8234 1.99099C49.4293 9.09696 46.8886 17.4122 43.0707 24.0426C35.0272 38.01 21.1141 47.4665 5.21739 49.7899C4.1712 49.9394 2.55435 50.1024 1.65761 50.1567C0.747283 50.1975 0 50.279 0 50.3334C0 50.3877 0.747283 50.4692 1.65761 50.51C2.55435 50.5644 4.1712 50.7274 5.21739 50.8769C21.1141 53.2002 35.0272 62.6567 43.0707 76.6241C46.8886 83.2546 49.4293 91.5698 49.8234 98.6758C49.8641 99.5861 49.9457 100.333 50 100.333C50.0543 100.333 50.1359 99.5861 50.1766 98.6758C50.5707 91.5698 53.1114 83.2546 56.9293 76.6241C64.9728 62.6567 78.8859 53.2002 94.7826 50.8769C95.8288 50.7274 97.4456 50.5644 98.3424 50.51C99.2527 50.4692 100 50.3877 100 50.3334C100 50.279 99.2527 50.1975 98.3424 50.1567C97.4456 50.1024 95.8288 49.9394 94.7826 49.7899C78.8859 47.4665 64.9728 38.01 56.9293 24.0426C53.1114 17.4122 50.5707 9.09696 50.1766 1.99099C50.1359 1.08066 50.0543 0.333377 50 0.333377C49.9457 0.333377 49.8641 1.08066 49.8234 1.99099Z"
                class="fill-current"
              />
            </svg>
          </span>
        </template>
      </div>
    </div>

    <!-- Row 2 (Moves Right) -->
    <div class="marquee-track-reverse flex whitespace-nowrap py-3">
      <div class="marquee-content-reverse flex items-center shrink-0">
        <template v-for="item in itemsRow2" :key="item">
          <span
            class="sm:heading-1 mx-6 flex items-center text-3xl font-bold uppercase tracking-tight text-flax-smoke-400/80 md:mx-10"
          >
            {{ item }}
            <svg
              class="ml-6 mr-2 inline-block size-6 sm:size-10 text-flax-smoke-500/60"
              viewBox="0 0 100 101"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M49.8234 1.99099C49.4293 9.09696 46.8886 17.4122 43.0707 24.0426C35.0272 38.01 21.1141 47.4665 5.21739 49.7899C4.1712 49.9394 2.55435 50.1024 1.65761 50.1567C0.747283 50.1975 0 50.279 0 50.3334C0 50.3877 0.747283 50.4692 1.65761 50.51C2.55435 50.5644 4.1712 50.7274 5.21739 50.8769C21.1141 53.2002 35.0272 62.6567 43.0707 76.6241C46.8886 83.2546 49.4293 91.5698 49.8234 98.6758C49.8641 99.5861 49.9457 100.333 50 100.333C50.0543 100.333 50.1359 99.5861 50.1766 98.6758C50.5707 91.5698 53.1114 83.2546 56.9293 76.6241C64.9728 62.6567 78.8859 53.2002 94.7826 50.8769C95.8288 50.7274 97.4456 50.5644 98.3424 50.51C99.2527 50.4692 100 50.3877 100 50.3334C100 50.279 99.2527 50.1975 98.3424 50.1567C97.4456 50.1024 95.8288 49.9394 94.7826 49.7899C78.8859 47.4665 64.9728 38.01 56.9293 24.0426C53.1114 17.4122 50.5707 9.09696 50.1766 1.99099C50.1359 1.08066 50.0543 0.333377 50 0.333377C49.9457 0.333377 49.8641 1.08066 49.8234 1.99099Z"
                class="fill-current"
              />
            </svg>
          </span>
        </template>
      </div>
      <div class="marquee-content-reverse flex items-center shrink-0" aria-hidden="true">
        <template v-for="item in itemsRow2" :key="item + '-clone'">
          <span
            class="sm:heading-1 mx-6 flex items-center text-3xl font-bold uppercase tracking-tight text-flax-smoke-400/80 md:mx-10"
          >
            {{ item }}
            <svg
              class="ml-6 mr-2 inline-block size-6 sm:size-10 text-flax-smoke-500/60"
              viewBox="0 0 100 101"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M49.8234 1.99099C49.4293 9.09696 46.8886 17.4122 43.0707 24.0426C35.0272 38.01 21.1141 47.4665 5.21739 49.7899C4.1712 49.9394 2.55435 50.1024 1.65761 50.1567C0.747283 50.1975 0 50.279 0 50.3334C0 50.3877 0.747283 50.4692 1.65761 50.51C2.55435 50.5644 4.1712 50.7274 5.21739 50.8769C21.1141 53.2002 35.0272 62.6567 43.0707 76.6241C46.8886 83.2546 49.4293 91.5698 49.8234 98.6758C49.8641 99.5861 49.9457 100.333 50 100.333C50.0543 100.333 50.1359 99.5861 50.1766 98.6758C50.5707 91.5698 53.1114 83.2546 56.9293 76.6241C64.9728 62.6567 78.8859 53.2002 94.7826 50.8769C95.8288 50.7274 97.4456 50.5644 98.3424 50.51C99.2527 50.4692 100 50.3877 100 50.3334C100 50.279 99.2527 50.1975 98.3424 50.1567C97.4456 50.1024 95.8288 49.9394 94.7826 49.7899C78.8859 47.4665 64.9728 38.01 56.9293 24.0426C53.1114 17.4122 50.5707 9.09696 50.1766 1.99099C50.1359 1.08066 50.0543 0.333377 50 0.333377C49.9457 0.333377 49.8641 1.08066 49.8234 1.99099Z"
                class="fill-current"
              />
            </svg>
          </span>
        </template>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
  const itemsRow1 = [
    'UI/UX DESIGN',
    'FULL-STACK DEVELOPMENT',
    'FIGMA PROTOTYPING',
    'CREATIVE WEB EXPERIENCES',
    'DESIGN SYSTEMS',
  ];

  const itemsRow2 = [
    'FRONTEND ARCHITECTURE',
    'MOTION & GSAP ANIMATIONS',
    'SCALABLE APPLICATIONS',
    'PERFORMANCE OPTIMIZATION',
    'API & DATABASE INTEGRATION',
  ];
</script>

<style scoped>
  .marquee-track {
    display: flex;
    overflow: hidden;
    user-select: none;
    gap: 0;
  }

  .marquee-content {
    animation: scroll-left 35s linear infinite;
  }

  .marquee-track-reverse {
    display: flex;
    overflow: hidden;
    user-select: none;
    gap: 0;
  }

  .marquee-content-reverse {
    animation: scroll-right 40s linear infinite;
  }

  @keyframes scroll-left {
    from {
      transform: translateX(0);
    }
    to {
      transform: translateX(-100%);
    }
  }

  @keyframes scroll-right {
    from {
      transform: translateX(-100%);
    }
    to {
      transform: translateX(0);
    }
  }

  .marquee-track:hover .marquee-content,
  .marquee-track-reverse:hover .marquee-content-reverse {
    animation-play-state: paused;
  }
</style>
