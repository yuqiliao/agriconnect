<script>
    import { onMount } from "svelte";
    import gsap from "gsap";
    import { ScrollTrigger } from "gsap/ScrollTrigger";

    gsap.registerPlugin(ScrollTrigger);

    onMount(() => {
        gsap.utils.toArray(".testimonial-card").forEach((card, i) => {
            gsap.fromTo(
                card,
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
                        trigger: card,
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
    id="testimonials"
    class="min-h-screen flex items-center justify-center bg-gray-500 py-12"
>
    <div class="container mx-auto px-6">
        <div class="text-center mb-12">
            <h2 class="text-3xl font-bold mb-4 text-white">
                What Our Users Are Saying
            </h2>
        </div>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <div class="testimonial-card bg-white p-6 rounded-lg shadow-md">
                <p class="text-xl italic mb-4">
                    "The voice feature is quite useful, providing a seamless
                    interaction that greatly benefits our operations."
                </p>
                <p class="text-right text-gray-700 font-bold">- User 1</p>
            </div>
            <div class="testimonial-card bg-white p-6 rounded-lg shadow-md">
                <p class="text-xl italic mb-4">
                    "The tool shows great promise in solidifying learning. The
                    voice feature is particularly effective."
                </p>
                <p class="text-right text-gray-700 font-bold">- User 2</p>
            </div>
            <div class="testimonial-card bg-white p-6 rounded-lg shadow-md">
                <p class="text-xl italic mb-4">
                    "Really great tool – I'm sure we can find many valuable
                    uses."
                </p>
                <p class="text-right text-gray-700 font-bold">- User 3</p>
            </div>
        </div>
    </div>
</section>

<style>
    .testimonial-card {
        opacity: 0;
    }
</style>
