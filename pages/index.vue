<template>
  <div>
    <div>
      <h2>About Myself</h2>
      <p>
        Hello everyone! NectoJ here. I’m a developer apprentice from the snowy
        alps of Zürich, Switzerland. I have a fond interest when it comes to
        learning programming, technologies, tools and frameworks. You’ll
        discover some of my various blog posts on this website regarding my
        current projects, ideas, reviews, writings, et cetera.
      </p>
    </div>
    <div class="updates">
      <div>
        <h2>Recent Updates</h2>
        <li v-for="article of articles" :key="article.slug">
          <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
            <p>{{ article.title }}</p>
          </NuxtLink>
        </li>
      </div>
      <div>
        <h2>Tags</h2>
        <li v-for="tag of tags" :key="tag.tag">
          <NuxtLink :to="{ name: 'blog-tags-tag', params: { tag: tag.name.toLowerCase() } }">
            <p>{{ tag.name }}</p>
          </NuxtLink>
        </li>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content("articles", params.slug)
      .only(["title", "description", "img", "slug", "author"])
      .sortBy("createdAt", "asc")
      .limit(10)
      .fetch();

    const tags = await $content("tags", params.tag)
      .only(["name"])
      .sortBy("name", "asc")
      .fetch();

    return {
      articles,
      tags,
    };
  },
};
</script>

<style scoped>
.recent-blogs {
}

.updates {
  display: inline-flex;
  width: 100%;
}

.updates > div {
  width: 50%;
}
</style>