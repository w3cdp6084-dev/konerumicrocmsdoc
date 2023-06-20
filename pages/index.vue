<template>
    <div>
        <ul>
            <li v-for="blog in data?.contents" :key="blog.id" class="card">
                <NuxtLink :to="`/${blog.id}`">
                    <img
                        :src="blog.eyecatch?.url"
                        :width="blog.eyecatch?.width"
                        :height="blog.eyecatch?.height"
                        alt=""
                    />
                    <div>
                        <div>
                        {{ blog.category?.name }}
                        </div>
                        <div>
                        {{ blog.title }}
                        </div>
                        <div>
                            {{ dateFormat(blog.publishedAt ?? blog.createdAt) }}
                        </div>
                    </div>
                </NuxtLink>
            </li>
        </ul>
    </div>
</template>

<script setup lang="ts">
    import {Blog} from "~/types/blog"
    const {data} = await useMicroCMSGetList<Blog>({
        endpoint : "blogs",
    })
</script>