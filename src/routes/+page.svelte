<script>
  import Header from "$lib/components/Header.svelte";

  let currentSlide = $state(0);

  const heroSlides = [
    {
      image: "/assets/home/main1.jpg",
      title: "AI-Driven Discovery",
      subtitle: "Revolutionizing Drug Development",
      gradientColor: "#1B211A",
    },
    {
      image: "/assets/home/main2.jpg",
      title: "Automated Synthesis",
      subtitle: "10,000 Compounds Per Day",
      gradientColor: "#316952",
    },
    {
      image: "/assets/home/main3.jpg",
      title: "Machine Learning",
      subtitle: "Continuous Model Evolution",
      gradientColor: "#020F1D",
    },
    {
      image: "/assets/home/main4.jpg",
      title: "High-Throughput Screening",
      subtitle: "Real-Time Validation",
      gradientColor: "#1B211A",
    },
  ];

  function nextSlide() {
    currentSlide = (currentSlide + 1) % heroSlides.length;
  }

  function prevSlide() {
    currentSlide = (currentSlide - 1 + heroSlides.length) % heroSlides.length;
  }

  function goToSlide(index) {
    currentSlide = index;
  }
</script>

<svelte:head>
  <title>ArrAI - AI-Driven Drug Discovery</title>
</svelte:head>

<Header />

<main>
  <section class="relative h-screen w-full">
    {#each heroSlides as slide, i}
      <div
        class={`absolute inset-0 transition-opacity duration-1000 ${i === currentSlide ? "opacity-100" : "opacity-0"}`}
      >
        <img
          src={slide.image}
          alt={slide.title}
          class="w-full h-full object-cover"
        />
        <div class="absolute inset-0 bg-black/40"></div>
      </div>
    {/each}

    <div
      class="absolute inset-0 flex flex-col items-center justify-center text-white z-10"
    >
      <div class="absolute top-1/2 left-32 -translate-y-1/2 text-left max-w-md">
        <p class="text-lg font-medium mb-3">
          {currentSlide + 1} / {heroSlides.length}
        </p>
        <h2 class="text-3xl font-medium mb-2">
          {heroSlides[currentSlide].title}
        </h2>
        <p class="text-xl font-light opacity-90">
          {heroSlides[currentSlide].subtitle}
        </p>
      </div>

      <div class="absolute bottom-40 left-0 right-0">
        <h1
          class="text-[14rem] font-bold leading-none text-center tracking-tight"
        >
          ArrAI
        </h1>
      </div>

      <a
        href="#mission"
        class="absolute bottom-24 right-24 text-base font-medium tracking-wide hover:underline transition-all"
      >
        Learn More
      </a>

      <div class="absolute bottom-24 left-1/2 -translate-x-1/2">
        <svg
          class="w-8 h-8"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M19 14l-7 7m0 0l-7-7m7 7V3"
          />
        </svg>
      </div>
    </div>

    <button
      onclick={prevSlide}
      class="absolute left-8 top-1/2 -translate-y-1/2 w-12 h-12 flex items-center justify-center bg-white/30 hover:bg-white/50 backdrop-blur-sm transition z-20"
      aria-label="Previous slide"
    >
      <svg
        class="w-5 h-5 text-white"
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M15 19l-7-7 7-7"
        />
      </svg>
    </button>

    <button
      onclick={nextSlide}
      class="absolute right-8 top-1/2 -translate-y-1/2 w-12 h-12 flex items-center justify-center bg-white/30 hover:bg-white/50 backdrop-blur-sm transition z-20"
      aria-label="Next slide"
    >
      <svg
        class="w-5 h-5 text-white"
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M9 5l7 7-7 7"
        />
      </svg>
    </button>

    <div class="absolute bottom-12 left-1/2 -translate-x-1/2 flex gap-3 z-20">
      {#each heroSlides as _, i}
        <button
          onclick={() => goToSlide(i)}
          class={`w-2.5 h-2.5 rounded-full transition ${i === currentSlide ? "bg-white" : "bg-white/40"}`}
          aria-label={`Go to slide ${i + 1}`}
        ></button>
      {/each}
    </div>
  </section>

  <section id="mission" class="relative" style="background-color: #E8EBE0;">
    <div
      class="absolute top-0 left-0 right-0 h-24 z-10 transition-all duration-1000 pointer-events-none"
      style={`background: linear-gradient(to bottom, ${heroSlides[currentSlide].gradientColor}, transparent);`}
    ></div>

    <div class="grid grid-cols-1 lg:grid-cols-2">
      <div class="relative h-screen">
        <img
          src="/assets/home/placeholder.png"
          alt="ArrAI Technology"
          class="w-full h-full object-cover"
        />
        <div
          class="absolute inset-0"
          style="background: linear-gradient(to bottom right, rgba(98, 129, 65, 0.2), rgba(139, 174, 102, 0.2));"
        ></div>
      </div>

      <div
        class="flex items-center justify-center p-20 lg:p-32 relative overflow-hidden"
      >
        <div
          class="absolute top-20 right-20 w-64 h-64 rounded-full opacity-20 blur-3xl"
          style="background-color: #8BAE66;"
        ></div>
        <div
          class="absolute bottom-20 left-20 w-96 h-96 rounded-full opacity-10 blur-3xl"
          style="background-color: #628141;"
        ></div>

        <div class="max-w-xl relative z-10">
          <div class="w-16 h-1 mb-8" style="background-color: #628141;"></div>
          <h2
            class="text-5xl font-bold mb-8 leading-tight"
            style="color: #1B211A;"
          >
            Harnessing AI for drug discovery
          </h2>
          <p
            class="text-xl leading-relaxed mb-8"
            style="color: #1B211A; opacity: 0.8;"
          >
            We partner with exceptional scientists to build the first automated
            high throughput drug synthesis-screening-training system
          </p>
          <a
            href="/about"
            class="inline-flex items-center gap-2 text-lg font-medium hover:opacity-70 transition"
            style="color: #628141;"
          >
            Learn more about our mission
            <svg
              class="w-5 h-5"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M17 8l4 4m0 0l-4 4m4-4H3"
              />
            </svg>
          </a>
        </div>
      </div>
    </div>
  </section>

  <section class="relative" style="background-color: #1B211A;">
    <div class="grid grid-cols-1 lg:grid-cols-2">
      <div
        class="flex items-center justify-center p-20 lg:p-32 text-white order-2 lg:order-1 relative overflow-hidden"
      >
        <div class="absolute top-0 left-0 w-full h-full opacity-10">
          <div
            class="absolute top-20 left-20 w-72 h-72 border-2 rounded-full"
            style="border-color: #8BAE66;"
          ></div>
          <div
            class="absolute bottom-20 right-20 w-96 h-96 border-2 rounded-full"
            style="border-color: #628141;"
          ></div>
        </div>

        <div class="max-w-xl relative z-10">
          <div class="w-16 h-1 mb-8" style="background-color: #8BAE66;"></div>
          <h2 class="text-5xl font-bold mb-8 leading-tight">
            Building medicines of the future
          </h2>
          <p class="text-xl leading-relaxed mb-8" style="color: #EBD5AB;">
            Our ODAST platform closes the loop between chemistry, biology, and
            AI.
          </p>

          <div class="grid grid-cols-3 gap-6 mb-8">
            <div>
              <div class="text-3xl font-bold" style="color: #8BAE66;">10K</div>
              <div class="text-sm" style="color: #EBD5AB; opacity: 0.8;">
                compounds/day
              </div>
            </div>
            <div>
              <div class="text-3xl font-bold" style="color: #8BAE66;">10×</div>
              <div class="text-sm" style="color: #EBD5AB; opacity: 0.8;">
                cost reduction
              </div>
            </div>
            <div>
              <div class="text-3xl font-bold" style="color: #8BAE66;">4×</div>
              <div class="text-sm" style="color: #EBD5AB; opacity: 0.8;">
                faster results
              </div>
            </div>
          </div>

          <a
            href="/pricing"
            class="inline-flex items-center gap-2 text-lg font-medium hover:opacity-70 transition"
            style="color: #8BAE66;"
          >
            Stats and pricing
            <svg
              class="w-5 h-5"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M17 8l4 4m0 0l-4 4m4-4H3"
              />
            </svg>
          </a>
        </div>
      </div>

      <div class="relative h-screen order-1 lg:order-2">
        <img
          src="/assets/home/placeholder.png"
          alt="Drug Discovery Platform"
          class="block w-full h-full object-cover"
          style="transform: scaleY(calc((100% + 1px) / 100%)); transform-origin: top;"
        />
        <div
          class="absolute inset-0"
          style="background: linear-gradient(to top left, rgba(27, 33, 26, 0.3), transparent);"
        ></div>
      </div>
    </div>
  </section>

  <section class="relative" style="background-color: #628141;">
    <div class="grid grid-cols-1 lg:grid-cols-2">
      <div class="relative h-screen">
        <img
          src="/assets/home/placeholder.png"
          alt="ArrAI Team"
          class="w-full h-full object-cover"
        />
        <div
          class="absolute inset-0"
          style="background: linear-gradient(to bottom right, rgba(139, 174, 102, 0.3), rgba(27, 33, 26, 0.3));"
        ></div>
      </div>

      <div
        class="flex items-center justify-center p-20 lg:p-32 relative overflow-hidden"
      >
        <div
          class="absolute top-0 right-0 w-64 h-64 opacity-20 transform rotate-45"
          style="background-color: #8BAE66;"
        ></div>
        <div
          class="absolute bottom-0 left-0 w-80 h-80 opacity-20 rounded-full"
          style="background-color: #EBD5AB;"
        ></div>

        <div class="max-w-xl relative z-10 text-white">
          <div class="w-16 h-1 mb-8" style="background-color: #001400;"></div>
          <h2 class="text-5xl font-bold mb-8 leading-tight">
            Visionaries, scientists and builders
          </h2>
          <p class="text-xl leading-relaxed mb-8" style="color: #001400;">
            Our global team spans Dresden, Zurich, San Francisco, and Suzhou,
            uniting computation and experimentation.
          </p>

          <a
            href="/designers"
            class="inline-flex items-center gap-2 text-lg font-medium hover:opacity-70 transition"
            style="color: #001400;"
          >
            Learn more about our team
            <svg
              class="w-5 h-5"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M17 8l4 4m0 0l-4 4m4-4H3"
              />
            </svg>
          </a>
        </div>
      </div>
    </div>
  </section>

  <section
    class="relative h-screen flex items-center justify-center"
    style="background-color: #1B211A;"
  >
    <div class="absolute inset-0 flex items-center justify-center opacity-5">
      <div class="text-[20rem] font-bold text-white">ArrAI</div>
    </div>

    <div class="relative z-10 text-center">
      <h2 class="text-7xl font-bold mb-16 text-white">
        We want to hear from you
      </h2>
      <a
        href="/contact"
        class="inline-block px-16 py-6 text-xl font-medium transition hover:opacity-90"
        style="background-color: #8BAE66; color: #1B211A;"
      >
        Contact us
      </a>
    </div>
  </section>
</main>

<footer class="py-12" style="background-color: #1B211A; color: white;">
  <div class="container mx-auto px-12">
    <div class="flex flex-col md:flex-row justify-between items-center gap-6">
      <div class="text-sm opacity-70">© 2025 ArrAI. All rights reserved.</div>
      <div class="flex gap-8">
        <a
          href="/privacy"
          class="text-sm opacity-70 hover:opacity-100 transition"
          >Privacy Policy</a
        >
        <a href="/" class="text-sm opacity-70 hover:opacity-100 transition"
          >Social Media</a
        >
      </div>
    </div>
  </div>
</footer>
