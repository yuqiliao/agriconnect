<script>
  import { scrollTo } from "svelte-scrollto";
  import Hero from "./components/Hero.svelte";
  import Features from "./components/Features.svelte";
  import Impact from "./components/Impact.svelte";
  import Stakeholders from "./components/Stakeholders.svelte";
  import Testimonials from "./components/Testimonials.svelte";

  function scrollToSection(section) {
    scrollTo({ element: document.getElementById(section), offset: -100 });
  }
</script>

<div class="min-h-screen bg-gray-100 text-gray-900">
  <!-- Navigation Bar -->
  <nav class="bg-white shadow-md fixed w-full z-30 top-0 left-0">
    <div class="container mx-auto px-0 py-0">
      <div class="flex justify-between items-center p-3 mx-3">
        <div class="text-lg font-semibold">AgriConnect</div>
        <div class="flex space-x-4">
          <button on:click={() => scrollToSection("home")}>Home</button>
          <button on:click={() => scrollToSection("features")}
            >Chatbot Features</button
          >
          <button on:click={() => scrollToSection("testimonials")}
            >Testimonials</button
          >
        </div>
      </div>
    </div>
  </nav>

  <!-- Sections -->
  <Hero />
  <Features />
  <Impact />
  <Stakeholders />
  <Testimonials />

  <!-- Footer Section -->
  <footer class="bg-gray-800 text-white py-6">
    <div class="container mx-auto px-6 text-center">
      <p>Office address: 86-90 Paul Street, London, England, EC2A 4NE</p>
      <p>© 2024 Intaigent. All Rights Reserved.</p>
    </div>
  </footer>
</div>
