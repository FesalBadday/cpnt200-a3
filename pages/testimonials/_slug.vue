<template>
  <v-main>
    <v-container>
      <v-card elevation="11" max-width="350">
        <h3>{{ testimonial.quote }}</h3>
        <v-img :src="testimonial.author.avatar" />
        <p>- {{ testimonial.author.name }}</p>
      </v-card>
    </v-container>
  </v-main>
</template>
<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const testimonial = await $content(`testimonials/${params.slug}`).fetch();
      return {
        testimonial,
      };
    } catch (error) {
      error("No article found");
    }
  },
};
</script>