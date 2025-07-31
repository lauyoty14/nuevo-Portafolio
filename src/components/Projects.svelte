<section id="projects" class="w-full min-h-screen flex flex-col relative justify-center items-center py-25 overflow-hidden">
    <div class="flex flex-col w-full h-full max-w-7xl min-h-[400px] mx-auto px-4 sm:px-6 lg:px-8 pb-0 md:pb-20 relative z-10">
        <div class="w-full title pb-10 md:pb-20">
            <h2 class="text-2xl md:text-4xl pb-2 text-center" data-aos="fade-up" data-aos-delay="100" data-aos-once="true">Proyectos</h2>
            <div data-aos="fade-up" data-aos-delay="150" data-aos-once="true" class="text-center">
                <Badge text="✨ proyecto en los que estoy trabajando" hideBeam outerClass="mr-1 mb-2" class="text-sm md:text-md px-3 bg-(--ui-primary)" />
            </div>
        </div>
        <div class="flex flex-row flex-wrap -m-2 overflow-hidden {hideAll ? 'mask-linear-to-bottom h-[500px] md:h-[450px]' : 'h-auto'}">
            {#each projects as project, key}
                <div class="w-full sm:w-1/2 lg:w-1/3 p-2 flex justify-center" data-aos="zoom-in" data-aos-delay={300+(50 * key)} data-aos-once="true">
                    <ProjectCard project={project} />
                </div>
            {/each}
        </div>
        {#if hideAll}
            <div class="h-50 btn-con flex justify-center relative z-10 transition-all duration-500 ease-out {isHiding ? 'opacity-0' : 'opacity-100'}" data-aos="fade-up" data-aos-delay="600" data-aos-once="true">
                <Button btnclass="z-20 -top-20" withBeam class="px-8" onclick={seeMore}> Ver mas </Button>
            </div>
        {/if}
    </div>
</section>

<script>
    import ProjectCard from '@components/ui/ProjectCard.svelte';
    import Button from '@components/ui/Button.svelte';
    import Badge from '@components/ui/Badge.svelte';

    let hideAll = $state(true);
    let isHiding = $state(false);

    function seeMore() {
        isHiding = true;
        // Wait for the fade-out animation to complete before hiding the container
        setTimeout(() => {
            hideAll = false;
        }, 500);
    }
     
    const projects = [
        {
            name: "ElFurtivo",
            imgSrc: '/projects/elFurtivo.jpg',
            company: "Cuchillos El Furtivo",
            date: "Enero 2025 - Abril 2025",
            description: "Una pagina web tipo Ecommerce, donde puedes ver un catalogo de productos artesanales y comprarlos, ademas de poder administrarse por los administradores de la empresa.",
            url: "https://elfurtivo.shop",
            hasLiveDemo: true,
            role: "Desarrollador Full Stack, encargado de la creacion de la pagina web desde cero, utilizando SvelteKit y Django. Integrando funcionalidades de carrito de compras, gestion de usuarios y administracion de productos.",
        },
        {
            name: "JLF",
            imgSrc: '/projects/JLF-landingpage.jpg',
            company: "JLF",
            date: "junio 2025 - julio 2025",
            description: "Una landing page para una empresa industrial que ofrece servicios de automatizacion y control de procesos industriales. La pagina web esta diseñada para ser informativa y facil de navegar, con un enfoque en la presentacion de los servicios y proyectos de la empresa.",
            url: "",
            hasLiveDemo: false,
            role: "Desarrollador Frontend, encargado de la creacion de la pagina web utilizando SvelteKit. Integrando funcionalidades de formulario de contacto, presentacion de servicios y proyectos, y optimizacion para SEO.",
            
        },
        {
            name: "Sistema de Gestion de Emprendimientos",
            imgSrc: '/projects/InicioPc-sistema-de-gestion.png',
            company: "proyecto personal",
            date: "fines de 2024",
            description: "Un proyecto personal que consiste en un sistema de gestion de emprendimientos, donde puedes crear, administrar y gestionar tus productos. El sistema esta diseñado para ser facil de usar y personalizable, con un enfoque en la gestion de productos y graficos de ventas.",
            url: "",
            hasLiveDemo: false,
            role: "Desarrolle un sistema de gestion de emprendimientos utilizando SvelteKit y Django. Integrando funcionalidades de gestion de productos, graficos de ventas y personalizacion del sistema.",
        },
        {
            name: "Sistema de Gestion de Canchas",
            imgSrc: '/projects/inicioPC-gestion-canchas.png',
            company: "proyecto personal",
            date: "principios de 2024",
            description: "Un proyecto personal que consiste en un sistema de gestion de canchas, donde puedes crear, administrar y gestionar tus canchas. El sistema esta diseñado para ser facil de usar y personalizable, con un enfoque en la gestion de reservas y pagos.",
            url: "",
            hasLiveDemo: false,
            role: "Desarrolle un sistema de gestion de canchas utilizando SvelteKit y Django. Integrando funcionalidades de gestion de reservas, pagos y personalizacion del sistema.",
        },
    ];
</script>
