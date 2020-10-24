<template>
  <article>
    <h1>{{ article.title }}</h1>
    <br/>
    <p>{{ article.description }}</p>
    <br/>
    <p>Post last updated: {{ formatDate(article.updatedAt) }}</p>
    <br/>
    <p>Tags: {{ article.tags }}</p>
    <br/>
    <author :author="article.author" />
    <br/>
    <prev-next :prev="prev" :next="next" />
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content("articles", params.slug).fetch();

    const [prev, next] = await $content("articles")
      .only(["title", "slug"])
      .sortBy("createdAt", "asc")
      .surround(params.slug)
      .fetch();

    return {
      article,
      prev,
      next,
    };
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("en", options);
    },
  },
};
</script>

<style>
.nuxt-content h2 {
  font-weight: bold;
  font-size: 28px;
}
.nuxt-content h3 {
  font-weight: bold;
  font-size: 22px;
}
.nuxt-content p {
  margin-bottom: 20px;
}

.icon.icon-link {
  display: inline-block;
  width: 20px;
  height: 20px;
  background-size: 20px 20px;
}
</style>