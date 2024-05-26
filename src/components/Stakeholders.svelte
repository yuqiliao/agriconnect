<script>
    import { onMount } from "svelte";
    import gsap from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";

    gsap.registerPlugin(ScrollTrigger);

    onMount(() => {
        gsap.utils.toArray(".stakeholder-tile").forEach((tile, i) => {
            gsap.fromTo(
                tile,
                {
                    opacity: 0,
                    y: 50,
                },
                {
                    opacity: 1,
                    y: 0,
                    duration: 1,
                    delay: i * 0.2,
                    scrollTrigger: {
                        trigger: tile,
                        start: "top 80%",
                        end: "top 60%",
                        scrub: true,
                    },
                },
            );
        });
    });
</script>

<section
    id="stakeholders"
    class="min-h-screen flex items-center justify-center bg-green-100"
>
    <div class="container mx-auto px-6 py-12">
        <div class="text-center">
            <h2 class="text-3xl font-bold mb-8">
                A Tool for Every Stakeholder
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="bg-white p-6 rounded-lg shadow-md stakeholder-tile">
                    <div class="mb-4">
                        <!-- Placeholder for NGO icon -->
                        <div
                            class="bg-gray-300 w-12 h-12 mx-auto rounded-full"
                        ></div>
                    </div>
                    <h3 class="text-xl font-bold mb-2">NGOs</h3>
                    <p>
                        Enhance your educational programs, monitor their
                        effectiveness in real time, and distribute your
                        specialized content directly to farmers.
                    </p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-md stakeholder-tile">
                    <div class="mb-4">
                        <!-- Placeholder for Knowledge Providers icon -->
                        <div
                            class="bg-gray-300 w-12 h-12 mx-auto rounded-full"
                        ></div>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Knowledge Providers</h3>
                    <p>
                        Disseminate research and best practices more widely and
                        effectively using a platform tailored to the needs of
                        the farming community.
                    </p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-md stakeholder-tile">
                    <div class="mb-4">
                        <!-- Placeholder for Agribusinesses icon -->
                        <div
                            class="bg-gray-300 w-12 h-12 mx-auto rounded-full"
                        ></div>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Agribusinesses</h3>
                    <p>
                        Connect directly with farmers to promote products and
                        services that can transform their agricultural
                        activities, and share customized instructional content
                        to ensure proper usage and application.
                    </p>
                </div>
            </div>
        </div>
    </div>
</section>
