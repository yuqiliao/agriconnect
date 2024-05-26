<script>
    import { onMount } from "svelte";
    import gsap from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";
    import { phoneContainer, currentVideo } from "../stores/ui.js";
    import videoFeature2 from "../videos/feature2.mp4";
    import videoFeature3 from "../videos/feature3.mp4";
    import videoFeature4 from "../videos/feature4.mp4";
    import videoFeature5 from "../videos/feature5.mp4";

    gsap.registerPlugin(ScrollTrigger);

    let container;
    let video;
    let videoSources = [
        videoFeature2,
        videoFeature3,
        videoFeature4,
        videoFeature5,
    ];

    onMount(() => {
        phoneContainer.subscribe((value) => {
            container = value;
        });
        currentVideo.subscribe((value) => {
            video = value;
        });

        gsap.utils.toArray(".feature").forEach((feature, i) => {
            ScrollTrigger.create({
                trigger: feature,
                start: "top center", // Adjusted start position
                end: "top center",
                onEnter: () => changeVideo(i),
                onEnterBack: () => changeVideo(i),
            });

            gsap.fromTo(
                feature,
                {
                    opacity: 0,
                    y: 50,
                },
                {
                    opacity: 1,
                    y: 0,
                    duration: 1,
                    scrollTrigger: {
                        trigger: feature,
                        start: "top 80%",
                        end: "top 60%",
                        scrub: true,
                    },
                },
            );
        });

        // Add extra padding at the bottom of the features section to ensure the last feature reaches the middle of the phone container
        ScrollTrigger.create({
            trigger: "#features",
            start: "bottom bottom",
            end: "bottom+=100%",
            scrub: true,
            onLeave: () => {
                gsap.to(container, { opacity: 0, duration: 1 });
            },
            onEnterBack: () => {
                gsap.to(container, { opacity: 1, duration: 1 });
            },
        });

        function changeVideo(index) {
            if (video) {
                video.src = videoSources[index];
                video.play();
            }
        }
    });
</script>

<section
    id="features"
    class="min-h-screen flex flex-col justify-center bg-gray-300"
>
    <div
        class="container mx-auto px-6 py-12 grid grid-cols-1 md:grid-cols-3 gap-8"
    >
        <div class="md:col-span-2 space-y-64">
            <div class="feature text-xl mb-4">
                <h3 class="text-2xl font-bold mb-2">Accessible Anywhere</h3>
                <p>
                    Available on popular messaging apps, ensuring ease of use
                    and accessibility for farmers accustomed to these platforms.
                </p>
            </div>
            <div class="feature text-xl mb-4">
                <h3 class="text-2xl font-bold mb-2">Language-Inclusive</h3>
                <p>
                    Communicates in various local dialects, breaking down
                    language barriers and enhancing understanding. (Swahili
                    language)
                </p>
            </div>
            <div class="feature text-xl mb-4">
                <h3 class="text-2xl font-bold mb-2">Personalized Advice</h3>
                <p>
                    Utilizes advanced AI algorithms to provide specific
                    recommendations based on individual farming conditions and
                    queries.
                </p>
            </div>
            <div class="feature text-xl mb-4">
                <h3 class="text-2xl font-bold mb-2">
                    Voice Conversation Feature
                </h3>
                <p>
                    Enables farmers in direct voice conversations, providing an
                    intuitive and natural communication method that is
                    particularly beneficial for those with limited literacy
                    skills.
                </p>
            </div>
        </div>
        <div class="hidden md:block"></div>
        <!-- Placeholder for spacing -->
        <div class="h-64"></div>
    </div>
</section>
