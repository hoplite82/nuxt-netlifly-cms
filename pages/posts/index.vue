<template>
    <main>
        <h1>Good new Side</h1>
        <section v-if="posts" class="w-full max-w-5xl mx-auto">
            <h1 class="title">LinkeBlog</h1>
            <posts post-type="posts" :amount="10" />
        </section>
    </main>
</template>
<script>
export default {
    async asyncData({ $content, error }) {
        let posts;
        try {
            posts = await $content("posts").fetch();
        } catch (e) {
            error({ message: "Blog posts not found" });
        }
        return { posts };
    },
}
</script>