<template>
  <main>
    <section v-if="post">
      <nav class="mb-8" aria-label="go back">
        <router-back class="block" />
      </nav>

      <article>
     
        <h1 class="">{{ post.judul }}</h1>
        <p class="mt-1 mb-8 text-primary-600 dark:text-primary-400">{{ post.deskripsi }}</p>
      </article>
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let post;
    try {
      post = await $content("rups", params.rups).fetch();
    } catch (e) {
      error({ message: "Project not found" });
    }
    return { post };
  },
}
</script>
