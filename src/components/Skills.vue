<template>
    <section id="skills" class="py-12 px-4">
      <h2 class="text-4xl font-bold text-center text-white mb-8">
        My Skills
      </h2>
  
      <div class="grid md:grid-cols-2 lg:grid-cols-2 gap-8">
        <div data-aos="flip-left"
          v-for="category in Skills"
          :key="category.id"
          class="bg-[#111a3e] p-6 rounded-lg shadow-lg"
        >
          <h3 class="text-2xl text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary mb-4">
            {{ category.name }}
          </h3>
          <div>
            <div
              v-for="skill in category.skills"
              :key="skill.name"
              class="mb-4"
            >
              <div class="flex justify-between mb-2">
                <span class="text-white">{{ skill.name }}</span>
                <span class="text-white">{{ skill.width }}</span>
              </div>
              <div class="h-2 bg-[#131d30] rounded-full">
                <div
                  class="h-2 rounded-full bg-primary"
                  :style="`width: ${skill.width};`"
                ></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const Skills = ref([
    {
      id: 1,
      name: "Frontend Development",
      skills: [
        { name: "Vue Js", width: "85%" },
        { name: "JavaScript", width: "90%" },
        { name: "JQuery", width: "80%" },
        { name: "HTML", width: "95%" },
        { name: "CSS", width: "90%" },
        { name: "Bootstrap", width: "85%" }
      ]
    },
    {
      id: 2,
      name: "Backend Development",
      skills: [
        { name: "Java", width: "85%" },
        { name: "Spring Boot", width: "80%" },
        { name: "Kotlin", width: "75%" },
        { name: "PHP", width: "80%" },
        { name: "Laravel", width: "85%" },
        { name: "Docker & Kubernetes", width: "70%"}
      ],
    }
  ]);
  </script>
  