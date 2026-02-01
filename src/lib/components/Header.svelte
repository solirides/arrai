<script>
  let scrolled = $state(false);

  if (typeof window !== "undefined") {
    window.addEventListener("scroll", () => {
      scrolled = window.scrollY > 50;
    });
  }
</script>

<header
  class={`fixed top-0 left-0 right-0 z-50 transition-all duration-300 ${scrolled ? "bg-[#f0f2e9]" : "bg-transparent"}`}
>
  <div class="container mx-auto px-12">
    <div class="flex items-center justify-center h-24">
      <nav class="hidden lg:flex items-center gap-16">
        <a
          href="/"
          class={`text-lg font-medium tracking-wide hover:underline transition-all ${scrolled ? "text-black" : "text-white"}`}
          >Home</a
        >
        <a
          href="/about"
          class={`text-lg font-medium tracking-wide hover:underline transition-all ${scrolled ? "text-black" : "text-white"}`}
          >About</a
        >
        <a
          href="/pricing"
          class={`text-lg font-medium tracking-wide hover:underline transition-all ${scrolled ? "text-black" : "text-white"}`}
          >Pricing</a
        >
        <a
          href="/designers"
          class={`text-lg font-medium tracking-wide hover:underline transition-all ${scrolled ? "text-black" : "text-white"}`}
          >Designers</a
        >
        <a
          href="/contact"
          class={`px-10 py-3 text-lg font-medium tracking-wide transition-all ${scrolled ? "bg-black text-white hover:bg-gray-800" : "bg-white text-black hover:bg-gray-100"}`}
          >Contact</a
        >
      </nav>
    </div>
  </div>
</header>
