<template>
  <section>
    <nav>
      <h2>Articles</h2>
      <ul>
        <li v-for="post in posts" :key="post.slug">
          <NuxtLink :to="`blog/${post.slug}`">{{ post.title }}</NuxtLink>
        </li>
      </ul>

      <h2>Gallery</h2>
      <ul>
        <li v-for="gallery in galleries" :key="gallery.slug">
          <NuxtLink :to="`gallery/${gallery.slug}`">{{ gallery.title }}</NuxtLink>
        </li>
      </ul>

      <h2>Testimonial</h2>
      <ul>
        <li v-for="testimonial in testimonials" :key="testimonial.slug">
          <NuxtLink :to="`testimonials/${testimonial.slug}`">{{ testimonial.quote }}</NuxtLink>
        </li>
      </ul>
    </nav>
  </section>
</template>
<script>
export default {
  // fetch the data from the blog in the content folder
  async asyncData({ $content }) {
    const posts = await $content("blog").fetch();
    const galleries = await $content("gallery").fetch();
    const testimonials = await $content("testimonials").fetch();
    return {
      posts,
      galleries,
      testimonials,
    };
  },
};
</script>