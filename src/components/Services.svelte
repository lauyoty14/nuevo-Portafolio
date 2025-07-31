<section
  id="services"
  class="min-h-screen w-full flex flex-col relative justify-center items-center py-25 overflow-hidden"
>
  <div
    data-orientation="horizontal"
    role="separator"
    class="w-full absolute left-0 top-0 z-10"
  >
    <div class="w-full border-solid border-t border-(--ui-primary)/30"></div>
  </div>

  <div class="flex flex-row flex-wrap w-full h-full max-w-7xl min-h-[400px] mx-auto px-4 sm:px-6 lg:px-8 pb-0 md:pb-20 relative z-10">
    <div class="w-full title pb-10 md:pb-20">
      <h2
        class="text-2xl md:text-4xl pb-2"
        data-aos="fade-up"
        data-aos-delay="100"
      >
        Mis <span class="text-(--ui-primary)">Principales Funciones</span>
      </h2>
      <div data-aos="fade-up" data-aos-delay="150">
        <Badge
          text="✨ Servicios clave"
          hideBeam
          outerClass="mr-1 mb-2"
          class="text-sm md:text-md px-3 bg-(--ui-primary)"
        />
      </div>
    </div>

    <div class="flex flex-row flex-wrap -m-3">
      {#each services as service, idx}
        <div class="w-full sm:w-1/2 lg:w-1/3 p-3 flex justify-center">
          <Card class="min-h-[200px]" data-aos="fade-up" data-aos-delay={300 + 50 * idx}>
            {#snippet title()}
              <div
                class="bg-black text-base p-3 shadow-lg rounded-md flex justify-center items-center relative"
              >
                <BgDots
                  y={2}
                  width={8}
                  height={8}
                  class="[mask-image:radial-gradient(300px_circle_at_center,white,transparent)] opacity-20"
                />
                {service.title}
              </div>
            {/snippet}

            {#snippet content()}
              <p class="px-6 pt-0 pb-3">
                {service.content}
              </p>
            {/snippet}

            {#snippet footer()}
              <p class="text-sm font-medium mb-2 muted">Tech usado:</p>
              {#each service.tech as tech}
                <Badge text={tech} outerClass="mr-1 mb-2" class="bg-black" hideBeam />
              {/each}
            {/snippet}
          </Card>
        </div>
      {/each}
    </div>
  </div>

  <div
    data-orientation="horizontal"
    role="separator"
    class="w-full absolute left-0 bottom-0 z-10"
  >
    <div class="w-full border-solid border-t border-(--ui-primary)/50"></div>
  </div>

  <div class="w-full h-full absolute [mask-image:radial-gradient(1000px_circle_at_center,white,transparent)]">
    <BgDarkTiles
      r={30}
      c={30}
      class="w-full absolute top-0 left-0 z-0"
    />
  </div>
</section>

<script>
  import Card from '@components/ui/Card.svelte';
  import BgDarkTiles from '@components/ui/BgDarkTiles.svelte';
  import Badge from '@components/ui/Badge.svelte';
  import BgDots from '@components/ui/BgDots.svelte';

  // Tus funciones principales
  const services = [
    {
      title: 'Desarrollador Fullstack',
      content:
        'Diseño y desarrollo de aplicaciones completas, abarcando tanto el frontend como el backend. Me ocupo de la arquitectura, la integración de bases de datos y la creación de APIs para ofrecer soluciones end-to-end.',
      tech: [
        'Node.js',
        'Django',
        'Express',
        'SvelteKit',
        'MySQL',
        'MongoDB',
        'REST',
      ],
    },
    {
      title: 'Desarrollador Web',
      content:
        'Construcción de interfaces web responsivas y accesibles usando tecnologías modernas. Implemento buenas prácticas de UX, WAI-ARIA y optimización de rendimiento para una experiencia de usuario fluida.',
      tech: ['HTML5', 'CSS3', 'JavaScript', 'TailwindCSS', 'Svelte', 'Django', 'NODE.js'],
    },
    {
      title: 'Desarrollador de APIs',
      content:
        'Creación de APIs robustas y seguras siguiendo estándares REST. Implemento autenticación, autorización y validación de datos, además de optimizar endpoints para escalabilidad.',
      tech: ['Express', 'PostgreSQL', 'JWT'],
    },
  ];
</script>

<style>
  section {
    background: linear-gradient(to bottom, rgb(11 11 11), rgb(22 22 22)) no-repeat center center / cover;
  }
</style>
