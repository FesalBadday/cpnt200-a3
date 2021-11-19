<template>
  <div>
    <ul>
      <li v-for="testimonial in testimonials" :key="testimonial.slug">
        <NuxtLink v-bind:to="`testimonials/${testimonial.slug}`">{{ testimonial.quote }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const testimonials = await $content("testimonials").fetch();
    return {
      testimonials,
    };
  },
};
</script>
