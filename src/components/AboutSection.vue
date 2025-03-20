<template>
  <section class="text-white mt-18" id="about">
    <div class="absolute z-0 top-[93rem] inset-x-0 h-64 flex items-start">
      <div
        class="h-24 w-64 bg-gradient-to-br from-primary via-secondary blur-2xl to-[#570cac] opacity-20"
      ></div>
    </div>
    <div
      class="md:grid md:grid-cols-2 gap-8 items-top py-8 px-4 xl:gap-16 sm:py-16 xl:px-16 z-1"
    >
      <div data-aos="flip-right">
        <h2 class="text-4xl font-bold text-white text-left mb-8">
          My Education
        </h2>
        <div class="space-y-8 py-8">
          <div
            v-for="element in education"
            :key="element.id"
            class="flex items-center md:w-[80%] w-full rounded-xl bg-[#111a3e] shadow-lg border border-[#1f1641]"
          >
            <div class="w-1/4">
              <img
                src="https://img.icons8.com/ios-glyphs/60/ffffff/graduation-cap--v1.png"
                alt="graduation-cap--v1"
              />
            </div>
            <div class="w-3/4 pl-4">
              <h3
                class="text-2xl font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary lg:text-xl"
              >
                {{ element.School }}
              </h3>
              <p class="text-white">{{ element.program }}</p>
              <p class="text-white">{{ element.year }} - {{ element.end }}</p>
            </div>
          </div>
        </div>
      </div>
      <div
        class="mt-4 md:mt-0 text-left flex flex-col z-10 h-full"
        data-aos="flip-right"
      >
        <h2 class="text-4xl font-bold text-white md:text-center text-left mb-4">
          More
          <span
            class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary"
            >About</span
          >
          Me
        </h2>
        <p class="text-base lg:text-lg mt-8 py-8">
          I am a skilled software engineer specializing in Java and Spring Boot,
          with extensive experience in building scalable and efficient backend
          systems. I have contributed to enterprise-level projects for one of
          Myanmar's largest telecom companies and currently serve as a Team
          Leader, managing development projects and delivering innovative
          software solutions for insurance companies. My goal is to continuously
          advance my expertise and contribute to cutting-edge software
          innovations.
        </p>
        <div class="grid grid-cols-3 gap-4 max-w-lg pt-8">
          <div
            class="text-center rounded-xl bg-[#111a3e] shadow-lg border border-[#1f1641] p-3"
          >
            <h3 class="text-white font-bold text-xl sm:text-2xl lg:text-3xl">
              {{ clientsCount }}+
            </h3>
            <p class="text-sm sm:text-base text-gray-300">Happy Clients</p>
          </div>
          <div
            class="text-center rounded-xl bg-[#111a3e] shadow-lg border border-[#1f1641] p-3"
          >
            <h3 class="text-white font-bold text-xl sm:text-2xl lg:text-3xl">
              {{ projectsCount }}+
            </h3>
            <p class="text-sm sm:text-base text-gray-300">Projects</p>
          </div>

          <div
            class="text-center rounded-xl bg-[#111a3e] shadow-lg border border-[#1f1641] p-3"
          >
            <h3 class="text-white font-bold text-xl sm:text-2xl lg:text-3xl">
              {{ experienceYears }}+
            </h3>
            <p class="text-sm sm:text-base text-gray-300">Years Experience</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, nextTick } from "vue";

const experienceYears = ref(0);
const projectsCount = ref(0);
const clientsCount = ref(0);
const hasAnimated = ref(false);

const animateCount = (target, stateRef, speed = 50) => {
  let count = 0;
  const interval = setInterval(() => {
    if (count >= target) {
      stateRef.value = target;
      clearInterval(interval);
    } else {
      count += 1;
      stateRef.value = count;
    }
  }, speed);
};

const onScrollIntoView = (entries) => {
  const entry = entries[0];
  if (entry.isIntersecting && !hasAnimated.value) {
    animateCount(3, experienceYears, 70);
    animateCount(20, projectsCount, 70);
    animateCount(10, clientsCount, 70);
    hasAnimated.value = true;
  }
};

onMounted(() => {
  nextTick(() => {
    const observer = new IntersectionObserver(onScrollIntoView, {
      threshold: 0.5,
    });

    const aboutSection = document.getElementById("about");
    observer.observe(aboutSection);
  });
});

const education = ref([
  {
    id: 1,
    School: "University of People",
    program: "Bachelor Degree in Computer Science",
    year: "2023",
    end: "Currently Studying",
  },
  {
    id: 2,
    School: "MTU",
    program: "Bachelor of Engineering (Civil)",
    year: "2017",
    end: "2020",
  },
]);
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
