<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">articles</h1>
      <posts post-type="articles" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts;
    try {
      posts = await $content("articles").fetch();
    } catch (e) {
      error({ message: "Blog posts not found" });
    }
    return { posts };
  },
}
</script>
