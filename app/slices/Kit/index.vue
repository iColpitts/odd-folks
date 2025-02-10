<script setup lang="ts">
import type { Content } from "@prismicio/client";
import * as prismic from "@prismicio/client";


// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.KitSlice>([
    "slice",
    "index",
    "slices",
    "context",
  ]),
);
const { client } = usePrismic();

  // const { data: actions } = await useAsyncData("posts", () =>
  //   client.getAllByType("action")
  // );

</script>

<template>
  <section
    :data-slice-type="slice.slice_type"
    :data-slice-variation="slice.variation"
  >
    <h2>{{ slice.primary.title }}</h2>
    <template v-for="link in slice.primary.author" :key="link.key">
      <PrismicLink :field="link" />
    </template>
    <template v-for="item in slice.primary.actions">
      <p>{{ item }}</p>
    </template>
  </section>
</template>
