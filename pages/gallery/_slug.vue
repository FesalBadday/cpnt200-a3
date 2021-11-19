<template>
  <v-main>
    <v-container>
      <h2>{{ gallery.title }}</h2>
      <v-img width="600" :src="gallery.image" />
    </v-container>
  </v-main>
</template>
<script>
export default {
  async asyncData({ $content, params, error }) {
    try {
      const gallery = await $content(`gallery/${params.slug}`).fetch();
      return {
        gallery,
      };
    } catch (error) {
      error("No article found");
    }
  },
};
</script>