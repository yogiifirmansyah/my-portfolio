<script setup>
import { computed, ref } from "vue";

const selectedCategory = ref("All"); // Default to show all categories
const isModalOpen = ref(false); // To manage modal visibility
const currentProject = ref(null);
const currentImageIndex = ref(0); // Track the index of the current image in the slider

// Project data with category and image information
const projects = ref([
  { id: 1, category: "Website", name: "Project One", image: ["src/assets/images/pro1.jpg", "src/assets/images/pro2.jpg", "src/assets/images/pro3.jpg"] },
  { id: 2, category: "Mobile App", name: "Project Two", image: ["src/assets/images/pro1.jpg", "src/assets/images/pro2.jpg", "src/assets/images/pro3.jpg"] },
  { id: 3, category: "Figma", name: "Project Three", image: ["src/assets/images/pro1.jpg", "src/assets/images/pro2.jpg", "src/assets/images/pro3.jpg"] },
]);

// Function to filter projects based on selected category
const filterCategory = (category) => {
  selectedCategory.value = category;
};

// Computed property to return filtered projects
const filteredProjects = computed(() => {
  if (selectedCategory.value === "All") {
    return projects.value;
  }
  return projects.value.filter((project) => project.category === selectedCategory.value);
});

// Fungsi untuk membuka modal
const openModal = (index) => {
  currentProject.value = projects.value[index];
  currentImageIndex.value = 0; // Set gambar pertama saat modal dibuka
  isModalOpen.value = true;
  console.log(index);
  console.log(currentProject.value);
};

// Fungsi untuk menutup modal
const closeModal = () => {
  isModalOpen.value = false;
  currentProject.value = null;
};

// Fungsi untuk navigasi gambar sebelumnya
const prevImage = () => {
  if (currentImageIndex.value > 0) {
    currentImageIndex.value--;
  } else {
    currentImageIndex.value = currentProject.value.image.length - 1; // Loop ke gambar terakhir
  }
};

// Fungsi untuk navigasi gambar berikutnya
const nextImage = () => {
  if (currentImageIndex.value < currentProject.value.image.length - 1) {
    currentImageIndex.value++;
  } else {
    currentImageIndex.value = 0; // Loop ke gambar pertama
  }
};
</script>

<template>
  <section id="projects" class="container min-h-screen flex-center">
    <div class="text-center text-balance">
      <h3>My Projects</h3>
      <p class="px-2 mt-3 text-gray-500">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Vitae, veritatis! Quaerat odio molestias, quam aspernatur repudiandae sed voluptas praesentium obcaecati illo, a in quis, cum magni totam explicabo deleniti vitae?
      </p>
      <br />
      <!-- <div class="flex-center gap-4">
        <button class="btn" :class="{ 'btn-filled': selectedCategory === 'All' }" @click="filterCategory('All')">All</button>
        <button class="btn" :class="{ 'btn-filled': selectedCategory === 'Website' }" @click="filterCategory('Website')">Website</button>
        <button class="btn" :class="{ 'btn-filled': selectedCategory === 'Mobile App' }" @click="filterCategory('Mobile App')">Mobile App</button>
        <button class="btn" :class="{ 'btn-filled': selectedCategory === 'Figma' }" @click="filterCategory('Figma')">Figma</button>
      </div>
      <br />
      <transition-group
        name="project-fade"
        tag="div"
        class="*:size-full *:object-cover *:border-4 *:dark:border-white *:rounded-md gap-4 *:cursor-pointer *:duration-1000 mx-auto max-w-4xl grid md:grid-rows-2 md:grid-cols-2 md:px-0 px-10 hover:*:cursor-zoom-in hover:*:scale-105"
      >
        <img @click="openModal(index)" v-for="(project, index) in filteredProjects" :key="project.id" :src="project.image[0]" :alt="project.category" />
      </transition-group> -->
      <div class="gap-4 mx-auto max-w-4xl grid md:grid-rows-2 md:grid-cols-3 md:px-0 px-10">
        <a href="" class="size-full object-cover border-4 dark:border-white rounded-md cursor-pointer duration-1000 hover:cursor-zoom-in hover:scale-105">
          <img src="../assets/images/pro1.jpg" alt="" />
          <div class="text-left text-balance p-2">
            <h1 class="font-semibold">Project Name</h1>
            <p class="text-xs font-light mt-2">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto ipsum maxime quod quos, rem quae nemo eveniet delectus excepturi illo nesciunt harum quidem? Reiciendis, non perferendis facilis quasi id illo?
            </p>
          </div>
        </a>
        <a href="" class="size-full object-cover border-4 dark:border-white rounded-md cursor-pointer duration-1000 hover:cursor-zoom-in hover:scale-105">
          <img src="../assets/images/pro2.jpg" alt="" />
          <div class="text-left text-balance p-2">
            <h1 class="font-semibold">Project Name</h1>
            <p class="text-xs font-light mt-2">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Iusto ipsum maxime quod quos, rem quae nemo eveniet delectus excepturi illo nesciunt harum quidem? Reiciendis, non perferendis facilis quasi id illo?
            </p>
          </div>
        </a>
        <a href="" class="size-full object-cover border-4 dark:border-white rounded-md cursor-pointer duration-1000 hover:cursor-zoom-in hover:scale-105">
          <img src="../assets/images/pro3.jpg" alt="" />
          <div class="text-left text-balance p-2">
            <h1 class="font-semibold">Project Name</h1>
            <p class="text-xs font-light mt-2">
              Lorem ipsum dolor sit amet consecteturr adipisicing elit. Iusto ipsum maxime quod quos, rem quae nemo eveniet delectus excepturi illo nesciunt harum quidem? Reiciendis, non perferendis facilis quasi id illo?
            </p>
          </div>
        </a>
      </div>
    </div>

    <!-- Modal -->
    <div v-show="isModalOpen" class="fixed inset-0 bg-black bg-opacity-75 flex-center z-[1000]">
      <div class="p-4 relative max-w-xl w-full bg-white rounded-lg overflow-hidden scroll">
        <button class="btn bg-slate-800 h-8 w-8 rounded-full absolute top-0 right-0 text-white" @click="closeModal">X</button>
        <div class="flex items-center justify-between relative">
          <!-- Previous Button -->
          <button @click="prevImage" class="btn bg-slate-800 h-8 w-8 text-white rounded-full absolute left-0">
            <i class="fa-solid fa-arrow-left"></i>
          </button>

          <!-- Image Display -->
          <img :src="currentProject?.image[currentImageIndex]" class="w-full h-auto" />

          <!-- Next Button -->
          <button @click="nextImage" class="btn bg-slate-800 h-8 w-8 text-white rounded-full absolute right-0">
            <i class="fa-solid fa-arrow-right"></i>
          </button>
        </div>
        <h3 class="text-gray-800 text-2xl font-semibold my-2">
          {{ currentProject?.name }}
        </h3>
        <p class="text-gray-600 font-normal text-xs">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Qui, neque rerum similique enim fugiat rem vitae alias accusamus facilis asperiores quo excepturi eos saepe eveniet reiciendis! Obcaecati libero ad omnis!
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Animation for project filtering */

.project-fade-enter-active,
.project-fade-leave-active {
  transition: transform 0.5s, opacity 0.5s;
}
.project-fade-enter,
.project-fade-leave-to {
  transform: translateY(30px);
  opacity: 0;
}
</style>
