<template>
  <main>
    <section v-if="post">
      <nav class="mb-8" aria-label="go back">
        <router-back class="block" />
      </nav>

      <article>
        <img
          v-if="post.gambar"
          class="cover-image"
          :src="post.gambar"
        >
        <!-- <h6 class="inline py-1 px-2 mr-1 bg-gray text-white text-sm font-medium rounded-sm">{{ post.kategori }}</h6> -->
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
      post = await $content("rups", params.project).fetch();
    } catch (e) {
      error({ message: "Project not found" });
    }
    return { post };
  },
}
</script>
