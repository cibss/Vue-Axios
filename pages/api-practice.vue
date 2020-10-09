<template>
  <div class="container">
    <div>
        <h1>API Practice</h1>
        <div v-for="testi in testimonial" :key="testi.id">
            <!-- <img src="{{ testi.photo.url }}"/> -->
            <p>{{ testi.title }}</p>
            <p>{{ testi.userName }}</p>
            <p>{{ testi.category }}</p>
            <p>{{ testi.excerpt }}</p>
        </div>
        
    </div>
  </div>
</template>

<script>
export default {
    async asyncData({ $axios }) {
        const testimonial  = await $axios.get('http://localhost:3000/api/fe/web/testimonials')
        return {
            testimonial: testimonial.data
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
</style>
