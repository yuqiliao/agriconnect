<script>
    import { onMount } from "svelte";
    import gsap from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";

    gsap.registerPlugin(ScrollTrigger);

    onMount(() => {
        gsap.utils.toArray(".impact-tile").forEach((tile, i) => {
            const timeline = gsap.timeline({
                scrollTrigger: {
                    trigger: tile,
                    start: "top 80%",
                    end: "top center",
                    toggleActions: "play none none reverse",
                    // markers: true,
                },
            });

            timeline.fromTo(
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
                },
            );
        });
    });
</script>

<section
    id="impact"
    class="min-h-screen flex items-center justify-center bg-blue-100"
>
    <div class="container mx-auto px-6 py-12">
        <div class="text-center">
            <h2 class="text-3xl font-bold mb-8">
                Enhanced Outreach and Impact
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div class="bg-white p-6 rounded-lg shadow-md impact-tile">
                    <h3 class="text-xl font-bold mb-2">Scalable Solutions</h3>
                    <p>
                        Whether addressing the needs of a small community or
                        scaling up to national programs, AgriConnect's flexible
                        architecture adapts to your scope and requirements.
                    </p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-md impact-tile">
                    <h3 class="text-xl font-bold mb-2">Data-Driven Insights</h3>
                    <p>
                        Gain valuable insights into the needs and behaviors of
                        farmers, allowing for more targeted and effective
                        interventions.
                    </p>
                </div>
            </div>
        </div>
    </div>
</section>
