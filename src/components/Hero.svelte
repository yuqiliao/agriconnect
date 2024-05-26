<script>
    import { onMount } from "svelte";
    import gsap from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";
    import { scrollTo } from "svelte-scrollto";
    import { phoneContainer, currentVideo } from "../stores/ui.js";
    import iphoneScreen from "../images/iphone-screen.avif";
    import videoFeature1 from "../videos/feature1.mp4";

    gsap.registerPlugin(ScrollTrigger);

    let container;
    let video;

    onMount(() => {
        phoneContainer.set(container);
        currentVideo.set(video);

        gsap.from(container, {
            y: -50,
            opacity: 0,
            duration: 1,
        });

        const timeline = gsap.timeline({
            scrollTrigger: {
                trigger: "#home",
                start: "top top",
                endTrigger: "#features",
                end: "bottom bottom",
                scrub: true,
                pin: container,
                pinSpacing: false,
            },
        });

        timeline.to(container, { scale: 0.8, x: "0vw" });

        video.src = videoFeature1;
        video.play();
    });

    function scrollToFeatures() {
        scrollTo({
            element: document.getElementById("features"),
            offset: -100,
        });
    }
</script>

<section
    id="home"
    class="min-h-screen flex items-center justify-center bg-gray-200 relative"
>
    <div
        class="container mx-auto flex flex-col md:flex-row items-center justify-between px-6 py-12 relative z-10"
    >
        <div class="text-left md:w-1/2">
            <h1 class="text-4xl font-bold mb-4">
                Revolutionizing Extension Services with AgriConnect
            </h1>
            <p class="text-xl mb-6">
                With AgriConnect, we're committed to enhancing agricultural
                productivity and sustainability through advanced technology. Our
                AI-driven platform empowers NGOs, knowledge service providers,
                and agribusinesses to deliver superior extension services and
                disseminate their own training content, making a tangible impact
                on the ground.
            </p>
            <button
                class="bg-blue-500 text-white px-4 py-2 rounded-md"
                on:click={scrollToFeatures}
            >
                Learn More
            </button>
        </div>
        <div class="md:w-1/2 flex justify-center md:justify-end relative z-10">
            <div class="relative w-full max-w-xs" bind:this={container}>
                <img
                    src={iphoneScreen}
                    alt="Phone"
                    class="w-full relative z-20"
                />
                <video
                    autoplay
                    muted
                    loop
                    class="absolute top-0 left-0 w-full h-full object-cover px-3 py-3 rounded-[36px] z-10"
                    bind:this={video}
                >
                    <source src={videoFeature1} type="video/mp4" />
                    Your browser does not support the video tag.
                </video>
            </div>
        </div>
    </div>
</section>
