<template>
  <div class="container">
    <div>
        <!-- <h1>API Practice</h1> -->
    
        <VueSlickCarousel v-bind="settings" class="carousel">
            <div>
                <h5 class="left"> <b>APA KATA MEREKA</b> </h5>
                <b-row>
                    <b-col  v-for="testi in testimonial" :key="testi.id">
                        <b-card class="card-size" >
                            <b-card-text class="left">
                                <b> {{ testi.userName }} </b>
                            </b-card-text>

                            <b-card-text class="left">
                                {{ testi.excerpt }}
                            </b-card-text>
                        </b-card>
                    </b-col>
                </b-row>
            </div>
        </VueSlickCarousel>

        

        <!-- <div>
            <h5 class="left"> <b>APA KATA MEREKA</b> </h5>
            <b-row>
                <b-col v-for="testi in testimonial" :key="testi.id">
                    <b-card class="card-size mb-2" >
                        <b-img :src="require(`${testi.photo.small}`)"/>
                        <b-img :src="require(`${testi.photo.small}`)"/>
                        <b-card-text class="left">
                            <b> {{ testi.userName }} </b>
                        </b-card-text>

                        <b-card-text class="left">
                            {{ testi.excerpt }}
                        </b-card-text>
                    </b-card>
                </b-col>
            </b-row>
        </div> -->

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
            slide: 0,
            sliding: null,

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
        align-items: center;
        text-align: center;
    }

    .left{
        text-align: left;
        color: black;
    }

    p {
        font-size: 14px;
    }

    .card-size{
        width: 291px;
        height: 420px;
    }

</style>
