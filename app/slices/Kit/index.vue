<script setup lang="ts">
  import type { Content } from "@prismicio/client";
  import Action from "~/components/action.vue";
  import { ref } from 'vue'


// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
  const props = defineProps(
    getSliceComponentProps<Content.KitSlice>([
      "slice",
      "index",
      "slices",
      "context",
    ])
  );

  const { client } = usePrismic();

  const { data: actions } = await useAsyncData("posts", () =>
    client.getAllByType("action")
  );

  const open = ref(true);

  const handleOpen = () => {
    if (open.value) {
      open.value = false
      console.log(open.value)
      return
    }
    if (!open.value) {
      open.value = true
      console.log(open.value)
      return
    }
    console.log("none")
  }

</script>

<template>
  <section
    :data-slice-type="slice.slice_type"
    :data-slice-variation="slice.variation"
    class="kit"
    style="margin: 6em auto; max-width: 800px;"
  >
    <div class="kit-heading flex bg-black border-black border-2 text-white items-center">
      <div class="m-4 mx-2">
        <button @click="handleOpen" type="button" class="text-black bg-white border-2 hover:bg-black hover:text-white focus:ring-4 focus:outline-none focus:ring-orange-300 font-medium rounded-full text-sm p-2.5 text-center inline-flex items-center">
        <svg  xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="50" height="50" viewBox="0 0 50 50" fill="currentColor">
          <path v-if="!open" d="M 24 3.6347656 L 23.5 3.9238281 L 19.5 6.234375 L 19 6.5234375 L 19 7.0996094 L 19 14.607422 L 12.5 10.853516 L 12 10.564453 L 11.5 10.853516 L 7.5 13.164062 L 7 13.453125 L 7 14.029297 L 7 20.960938 L 7 21.537109 L 7.5 21.826172 L 19 28.466797 L 19 41.740234 L 19 42.316406 L 19.498047 42.605469 L 25.498047 46.076172 L 25.998047 46.365234 L 26.498047 46.076172 L 30.498047 43.765625 L 30.998047 43.476562 L 30.998047 42.900391 L 30.998047 35.392578 L 37.498047 39.146484 L 37.998047 39.435547 L 38.498047 39.146484 L 42.498047 36.835938 L 42.998047 36.546875 L 42.998047 35.970703 L 42.998047 29.039062 L 42.998047 28.462891 L 42.498047 28.173828 L 31 21.533203 L 31 8.2597656 L 31 7.6835938 L 30.501953 7.3945312 L 24.501953 3.9238281 L 24 3.6347656 z M 24 5.078125 L 29.5 8.2597656 L 26 10.277344 L 20.5 7.0996094 L 24 5.078125 z M 20.25 7.5332031 L 25.75 10.710938 L 25.75 24.423828 A 0.250025 0.250025 0 0 0 25.875 24.638672 L 37.75 31.496094 L 37.75 37.847656 L 30.125 33.443359 L 30.103516 33.431641 L 26.125 31.134766 A 0.250025 0.250025 0 0 0 25.980469 31.101562 A 0.250025 0.250025 0 0 0 25.75 31.351562 L 25.75 44.777344 L 20.25 41.595703 L 20.25 27.890625 A 0.250025 0.250025 0 0 0 20.125 27.673828 L 8.25 20.816406 L 8.25 14.462891 L 19.875 21.175781 A 0.250025 0.250025 0 0 0 20.25 20.958984 L 20.25 16.339844 L 20.25 7.5332031 z M 29.75 8.6933594 L 29.75 21.966797 L 26.25 23.990234 L 26.25 10.710938 L 29.75 8.6933594 z M 12 12.007812 L 19.75 16.484375 L 19.75 20.525391 L 8.4980469 14.03125 L 12 12.007812 z M 30 22.398438 L 41.501953 29.041016 L 38 31.0625 L 26.498047 24.421875 L 30 22.398438 z M 41.75 29.472656 L 41.75 35.826172 L 38.25 37.847656 L 38.25 31.496094 L 41.75 29.472656 z M 26.25 31.785156 L 29.75 33.804688 L 29.75 42.755859 L 26.25 44.777344 L 26.25 31.785156 z"></path>
          <path v-if="open" d="M 20.365234 3.4238281 L 19.5 3.9238281 L 15.5 6.234375 L 10.5 9.1230469 L 9.6347656 9.6230469 L 10.134766 10.490234 L 17.634766 23.482422 L 10.501953 27.59375 L 9.6347656 28.09375 L 10.134766 28.960938 L 14.134766 35.890625 L 14.634766 36.755859 L 15.501953 36.255859 L 22.634766 32.136719 L 30.134766 45.130859 L 30.634766 45.996094 L 31.501953 45.496094 L 36.501953 42.605469 L 40.501953 40.296875 L 41.367188 39.796875 L 40.867188 38.929688 L 33.367188 25.945312 L 40.501953 21.826172 L 41.367188 21.326172 L 40.867188 20.460938 L 36.867188 13.529297 L 36.367188 12.664062 L 35.501953 13.164062 L 28.367188 17.283203 L 20.867188 4.2890625 L 20.365234 3.4238281 z M 19.908203 5.1308594 L 27.658203 18.558594 L 24.091797 20.617188 L 16.341797 7.1914062 L 19.908203 5.1308594 z M 15.908203 7.4414062 L 23.783203 21.083984 A 0.250025 0.250025 0 0 0 24.125 21.175781 L 28.109375 18.875 A 0.250025 0.250025 0 0 0 28.125 18.867188 L 31.908203 16.681641 L 35.660156 23.177734 L 31.875 25.363281 A 0.250025 0.250025 0 0 0 31.853516 25.376953 L 27.875 27.669922 A 0.250025 0.250025 0 0 0 27.783203 28.011719 L 35.658203 41.648438 L 31.091797 44.289062 L 23.216797 30.644531 A 0.250025 0.250025 0 0 0 22.875 30.552734 L 15.091797 35.048828 L 11.341797 28.550781 L 19.125 24.066406 A 0.250025 0.250025 0 0 0 19.216797 23.724609 L 11.341797 10.082031 L 15.908203 7.4414062 z M 35.908203 14.371094 L 39.658203 20.869141 L 36.09375 22.927734 L 32.341797 16.431641 L 35.908203 14.371094 z M 31.908203 25.921875 L 39.658203 39.337891 L 36.091797 41.398438 L 28.341797 27.978516 L 31.908203 25.921875 z"></path>
        </svg>
        <span class="sr-only">Icon description</span>
      </button>
      </div>
      
      <div>
        <h1>{{ slice.primary.title }}</h1>
        <template v-for="link in slice.primary.author" :key="link.key">
          <PrismicLink :field="link" />
        </template>
      </div>
    </div>
    
    <div v-if="open" class="flex flex-wrap justify-between outline-1 outline-offset-5">
      <template v-for="item in slice.primary.actions">
      <Action v-if="actions" :data="actions.find((el) => el.id == item.action.id)" class="p-4 justify-around flex basis-1/3 flex-col h-fill align-between"></Action>
    </template>
    </div>
  </section>
</template>
