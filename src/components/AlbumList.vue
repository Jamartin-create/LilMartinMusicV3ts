<template>
  <div class="list-page">
    <div class="col-list">
      <AlbumItem
        v-for="item in props.list"
        :key="item.id"
        :id="item.id"
        :artist="item.artist"
        :artists="item.artists"
        :name="item.name"
        :size="item.size"
        :pic-url="item.pirUrl"
        :blur-pic-url="item.blurPicUrl"
      />
    </div>
    <button class="hover-button" @click="loadMore">
      {{
        noMore ? "没有更多啦" : props.loading ? "loading..." : "点击加载更多"
      }}
    </button>
  </div>
</template>

<script setup lang="ts">
import AlbumItem from "./AlbumItem.vue";

const props = defineProps<{
  list: any[];
  loading: boolean;
  noMore: boolean;
}>();
const emits = defineEmits(["loadMore"]);
function loadMore() {
  emits("loadMore");
}
</script>
