<template>
  <section
    id="home"
    class="min-h-screen container grid place-item-center relative before:absolute before:top-0 before:bg-heroLight before:size-full before:start-1/2 before:transform before:-translate-x-1/2 before:bg-no-repeat before:-z-[1] before:dark:bg-heroDark"
  >
    <div class="size-full pt-20 grid md:grid-cols-6 items-center justify-around max-w-6xl">
      <!-- Bagian Kiri -->
      <div class="lg:col-span-2 md:col-span-3 md:text-left text-center sm:pl-2">
        <!-- Intro and Button -->
        <div>
          <h5 class="font-medium text-gray-600 dark:text-gray-200">Hello Welcome</h5>
          <h1 class="sm:text-5xl text-4xl !leading-normal dark:text-white relative font-medium">
            I'm <span class="text-primary">Yogi</span><br />
            Website Developer
          </h1>
          <button class="btn btn-filled mt-5">
            <i class="fa-regular fa-envelope"></i>
            Hire Me
          </button>

          <button class="font-semibold dark:text-gray-200 border-b-2 border-gray-700 ml-4"><i class="fa-solid fa-up-right-from-square mr-1"></i>See Portfolio</button>
        </div>
        <!-- Lorem Text -->
        <div class="md:w-96 md:ml-auto flex mt-9 gap-2 dark:text-gray-300">
          <i class="fa-solid fa-border-all mt-0.5 md:inline-block hidden"></i>
          <p class="text-xs text-balance leading-5 max-w-md px-2 mx-auto">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Atque labore temporibus error, delectus adipisci consequuntur sint vitae aspernatur dicta vel molestias expedita autem corporis est officiis illo perferendis. Officia,
            aut?
          </p>
        </div>
        <!-- Social icons button -->
        <div class="flex items-center md:justify-end justify-center mt-9 gap-6 dark:text-gray-200 text-gray-600">
          <p class="text-xs">Follow Us</p>
          <div class="flex gap-3">
            <a href="#" class="social-icon">
              <i class="fa-brands fa-github"></i>
            </a>
            <a href="#" class="social-icon">
              <i class="fa-brands fa-linkedin"></i>
            </a>
            <a href="#" class="social-icon">
              <i class="fa-brands fa-facebook"></i>
            </a>
          </div>
        </div>
      </div>
      <!-- Bagian Tengah (Photo Profile) -->
      <div class="lg:col-span-2 md:col-span-3">
        <img src="../assets/images/person.png" class="md:w-full max-w-96 md:mt-0 mt-5 w-2/3 mx-auto" alt="" />
      </div>
      <!-- Bagian Kanan (Experience) -->
      <div class="lg:col-span-2 md:col-span-6 lg:bg-gradient-to-l md:bg-none bg-gradient-to-l from-gray-100 dark:from-slate-800 md:mt-0 mt-2 lg:h-96 md:h-auto h-96">
        <ul class="text-2xl leading-[3.14rem] text-center pt-5 lg:block md:flex items-center justify-between data-[slot=count]:*:text-3xl data-[slot=count]:*:font-bold">
          <li data-slot="count">12+</li>
          <li>Year of <span class="text-primary">Experience</span></li>
          <br />
          <li data-slot="count">8+</li>
          <li>Completed <span class="text-primary">Projects</span></li>
          <li>
            <button class="btn btn-outline mt-10 lg:mt-10 md:mt-0"><i class="fa-solid fa-download"></i>Download CV</button>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>
