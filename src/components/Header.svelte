<header class="flex fixed w-full top-0 left-1/2 transform -translate-x-1/2 z-50 md:backdrop-blur">
  <div class="flex justify-between items-center py-3 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full">
    <a href="/" class="block w-20 h-20 relative group">
      <img
        src="/logo-op-default.png"
        alt="Logo <OP/>"
        class="absolute inset-0 w-full h-full object-contain opacity-100 group-hover:opacity-0 transition duration-300"
      />
      <img
        src="/logo-op-hover.png"
        alt="Logo <OP/> Hover"
        class="absolute inset-0 w-full h-full object-contain opacity-0 group-hover:opacity-100 transition duration-300"
      />
    </a>

    <!-- Hamburger Menu Button -->
    <button
      class="md:hidden text-2xl focus:outline-none z-60 flex justify-center items-center"
      aria-label="Toggle navigation"
      on:click="{() => isMobileNavOpen = !isMobileNavOpen}"
      data-aos="fade-left"
      data-aos-delay="200"
    >
      {#if isMobileNavOpen}
        <XIcon size="30" />
      {:else}
        <AlignRightIcon size="30" />
      {/if}
    </button>

    <!-- Desktop Navigation -->
    <nav id="desktop-nav" class="hidden md:flex" data-aos="fade-left" data-aos-delay="200">
      {#each anchors as { label, slug }}
        <a
          href="#{slug}"
          class="{anchorClasses(slug)}"
          on:click="{e => handleClick(e, slug)}"
        >
          {label}
        </a>
      {/each}
    </nav>

    <!-- Mobile Navigation -->
    {#if isMobileNavOpen}
      <div id="mobile-nav" class="fixed top-14 right-8 bg-opacity-80 flex flex-col items-center justify-center z-50">
        {#each anchors as { label, slug }}
          <a
            href="#{slug}"
            class="{anchorClasses(slug, true)}"
            on:click="{e => handleClick(e, slug)}"
          >
            {label}
          </a>
        {/each}
      </div>
    {/if}
  </div>
</header>

<script>
  import { XIcon, AlignRightIcon } from '@lucide/svelte';

  // Estado simple en JS
  let isMobileNavOpen = false;
  let activeAnchor = 'Hero';

  // Array con label y slug (el slug debe coincidir con los id de tus <section>)
  const anchors = [
    { label: 'Sobre mi', slug: 'about' },
    { label: 'Puestos de trabajo', slug: 'services' },
    { label: 'Projectos', slug: 'projects' },
    { label: 'Contactame', slug: 'contact' },
  ];

  const defaultClasses = {
    desktop: 'text-lg font-semibold mx-4 hover:text-(--ui-primary) transition-colors duration-300',
    mobile:  'text-2xl bg-black rounded-full px-5 py-2 m-4 text-white hover:bg-(--ui-primary) transition-colors duration-300',
  };
  const activeClasses = {
    desktop: 'active bg-gradient-to-r from-(--ui-primary) to-indigo-600 bg-clip-text text-transparent',
    mobile:  'active bg-gradient-to-r from-(--ui-primary) to-indigo-600',
  };

  function getClass(obj, isMobile) {
    return isMobile ? obj.mobile : obj.desktop;
  }

  function anchorClasses(slug, isMobile = false) {
    return activeAnchor === slug
      ? `${getClass(defaultClasses, isMobile)} ${getClass(activeClasses, isMobile)}`
      : getClass(defaultClasses, isMobile);
  }

  // Al hacer click: previene el salto brusco, hace scroll suave y cierra el menú
  function handleClick(event, slug) {
    event.preventDefault();
    const section = document.getElementById(slug);
    if (section) {
      section.scrollIntoView({ behavior: 'smooth' });
      activeAnchor = slug;
      isMobileNavOpen = false;
    }
  }

  // Observer para actualizar activeAnchor al hacer scroll manual
  import { onMount } from 'svelte';
  onMount(() => {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          activeAnchor = entry.target.id;
        }
      });
    }, { threshold: 0.6 });

    document.querySelectorAll('section[id]').forEach(sec => observer.observe(sec));
    return () => observer.disconnect();
  });
</script>
