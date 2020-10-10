<template>
  <div class="container mt-5">
    <div>
    
        <VueSlickCarousel v-bind="settings" class="carousel">
            <div>
                <h5 class="mb-5"> <b>APA KATA MEREKA</b> </h5>
                <b-row>
                    <b-col  v-for="testi in testimonial" :key="testi.id">
                        <b-card class="card-size" >     
                            <b-avatar :src="testi.photo.url" size="lg" class="ava"/>
                            <b-card-text class="mt-4">
                                <b> {{ testi.userName }} </b>
                            </b-card-text>

                            <b-card-text>
                                {{ testi.excerpt }}
                            </b-card-text>
                        </b-card>
                    </b-col>
                </b-row>
            </div>
        </VueSlickCarousel>

    </div>
  </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
    name: 'api-practice',
    async asyncData({ $axios }) {
        const testimonial  = await $axios.get('http://localhost:3000/api/fe/web/testimonials')
        return {
            testimonial: testimonial.data
        }
    },
    components: {
        VueSlickCarousel 
    },
    data () {
        return {
            settings: {
                arrows: true,
                dots: true,
                rows: 1,
                slidesPerRow: 1,
                autoplay: false,
            }
        }
    }
}


</script>

<style>
    .container {
        margin: 0 auto;
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: left;
        text-align: left;
    }

    p {
        font-size: 14px;
    }

    .card-size{
        width: 291px;
        height: 420px;
    }

    .ava {
        position: absolute;
        top: -7%;
    }

</style>
