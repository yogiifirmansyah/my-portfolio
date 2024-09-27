<template>
  <section id="contact" class="container relative max-w-4xl mx-auto min-h-screen flex-center px-5">
    <div class="pb-10 md:pb-24">
      <div class="text-center">
        <h3>Contact Me</h3>
        <p class="px-2 mt-3 text-gray-500">
          Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quibusdam labore corrupti nisi impedit quidem beatae et fuga eum voluptatem ad, soluta aperiam aliquid reprehenderit atque rem ab error neque nesciunt.
        </p>
      </div>
      <div class="mt-12 md:relative flex flex-col gap-5 sm:max-w-full mx-auto max-w-xs">
        <div class="dark:bg-slate-800 bg-slate-50 dark:text-gray-100 text-gray-800 rounded-lg shadow-xl mx-auto md:w-2/3 w-full py-14 px-7">
          <h3>
            Send Us A <br />
            <span>Message</span>
          </h3>
          <form class="*:flex *:flex-col *:gap-1 mt-5 md:w-2/3 w-full">
            <div>
              <label for="name">Name</label>
              <input type="text" id="name" placeholder="Enter your name" />
            </div>
            <div>
              <label for="email">Email</label>
              <input type="text" id="email" placeholder="Enter your email" />
            </div>
            <div>
              <label for="message">Message</label>
              <textarea name="message" id="message" placeholder="Enter your message"></textarea>
            </div>
            <button class="btn btn-filled ml-auto">Send to Us</button>
          </form>
        </div>
        <div class="dark:bg-gray-700 bg-white py-12 px-7 md:absolute -right-3 rounded-xl shadow-xl md:w-2/5 h-6/7 top-28 w-full mx-auto">
          <h3 class="font-semibold text-2xl border-b pb-4 border-gray-600">Drop In Our <br />Office <span class="text-primary">.</span></h3>
          <div class="py-4">
            <p class="text-xs text-gray-400 leading-5">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Vel aliquam pariatur ut commodi eaque ullam corporis, autem inventore dolor quas nostrum, incidunt labore accusantium, reiciendis quidem mollitia facilis libero
              recusandae!
            </p>
            <ul class="*:flex *:gap-4 *:items-center *:mt-4">
              <li>
                <i class="fa-solid fa-location-dot"></i>
                <div>
                  <h2>YF Solution</h2>
                  <address>Bendotretek, Prambon, Sidoarjo</address>
                </div>
              </li>
              <li>
                <i class="fa-solid fa-envelope"></i>
                <p>yogifirmansyah1407@gmail.com</p>
              </li>
              <li>
                <i class="fa-solid fa-phone"></i>
                <p>083872287687</p>
              </li>
            </ul>
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
        </div>
      </div>
    </div>
  </section>
</template>
