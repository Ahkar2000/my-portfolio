<template>
  <section class="text-white mt-18" id="experiences">
    <div class="gap-8 items-center py-8 px-4 xl:gap-16 xl:px-16">
      <div data-aos="flip-left">
        <h2
          class="text-4xl font-bold text-white text-left mb-8 md:text-center md:mt-0 mt-8"
        >
          My Experiences
        </h2>

        <div class="space-y-8 py-8" data-aos="fade-left">
          <div
            v-for="(element, index) in Experiences"
            :key="element.id"
            class="flex flex-col rounded-xl p-4 bg-[#111a3e] shadow-lg border border-[#1f1641]"
          >
            <div class="flex items-center gap-4">
              <div class="w-16">
                <img
                  src="https://img.icons8.com/ios-filled/100/ffffff/lawyer.png"
                  alt="company"
                  class="w-full"
                />
              </div>
              <div class="flex-1">
                <h3
                  class="text-2xl font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary"
                >
                  {{ element.role }}
                </h3>
                <p class="text-white">{{ element.company }}</p>
                <p class="text-white">{{ element.date }}</p>
              </div>
              <button
                @click="toggleDetails(index)"
                class="text-white focus:outline-none"
              >
                <span
                  :class="expandedIndex === index ? 'rotate-180' : ''"
                  class="transition-transform"
                >
                  {{ expandedIndex === index ? "▲" : "▼" }}
                </span>
              </button>
            </div>

            <transition name="fade">
              <div
                v-if="expandedIndex === index"
                class="mt-4 text-white bg-[#1a2247] p-3 rounded-lg"
              >
                <p>
                  <strong>Job Description:</strong> {{ element.description }}
                </p>
                <p>
                  <strong>Technologies Used:</strong>
                  {{ element.technologies.join(", ") }}
                </p>
              </div>
            </transition>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";

const expandedIndex = ref(null);

const Experiences = ref([
  {
    id: 1,
    role: "Development Team Leader",
    company: "Ace Plus Solutions Company Limited",
    date: "Apr 2024 - Current",
    description:
      "Lead a team of three members and develop and design comprehensive system solutions and database design to meet the specific needs of insurance companies. Perform regular system updates, optimizations, and troubleshooting to ensure seamless operation. Resolve customer complaints promptly, providing effective solutions and maintaining high customer satisfaction.",
    technologies: ["Java EE", "Spring Boot", "JSF", "MSSQL", "Windows Server"],
  },
  {
    id: 2,
    role: "Backend Developer",
    company: "Telecom International Myanmar Company Limited",
    date: "Jan 2023 - Apr 2024",
    description:
      "Design system architecture, system flow, and database design of multiple projects. Collaborate with frontend and mobile teams to ensure clients’ requests. Update and maintain existing projects and implement new projects. Demonstrated strong expertise in server management by maintaining and deploying all services on CentOS 7 servers, ensuring system reliability and performance.",
    technologies: [
      "Java EE",
      "Spring Boot",
      "Redis",
      "Kafka",
      "Keycloak",
      "Oracle",
      "CentOS 7",
    ],
  },
  {
    id: 3,
    role: "Cloud Infrastructure Intern",
    company: "Non-Profit Organization",
    date: "Mar 2023 - June 2023",
    description:
      "Learned the basics of AWS Cloud Platform. Performed hands-on labs and real-world projects using AWS Cloud services.",
    technologies: ["AWS Cloud Platform", "Wizlabs"],
  },
  {
    id: 4,
    role: "Web Developer",
    company: "IME PLUS",
    date: "July 2022 - Jan 2023",
    description:
      "Designed and developed a POS project for a convenience store. Designed and developed a School Attendance System using QR Code for a private school. Collaborated with a developer to develop systems using PHP and Laravel.",
    technologies: ["PHP", "Laravel", "Vue.js", "MySQL"],
  },
]);

const toggleDetails = (index) => {
  expandedIndex.value = expandedIndex.value === index ? null : index;
};
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
