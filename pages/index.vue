<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Changelogs</h1>

      <ul>
        <li v-for="item in posts">
          {{ item.title }}
        </li>
      </ul>


    </section>
  </main>
</template>

<script>
export default {
  async asyncData({$content, error}) {
    let posts;
    try {
      posts = await $content("changelogs").fetch();
    } catch (e) {
      error({message: "Projects not found"});
    }
    return {posts};
  },
}
</script>
