<template>
  <div class="tab-pane">
    
    <div class="roadmap-card" :class="animated">
      <div class="roadmap-card-h flex">
          <img src="~/assets/phase-1.svg" alt="" v-if="items.index==1"/>
          <img src="~/assets/phase-2.svg" alt="" v-if="items.index==2"/>
          <img src="~/assets/phase-3.svg" alt="" v-if="items.index==3"/>
        <h1 class="small-side-mg roadmap-card-h-text" id="">
          {{ items.title }}
        </h1>
        <img src="~/assets/good.svg" alt="" class="good" v-if="items.index==2 || items.index==1" />
      </div>
      <div
        class="roadmap-card-b"
        v-for="(subitem, index) in items.content"
        :key="'subitems' + index"
        :class="subitem.subclass"
      >
        <h2 class="group-h-grad roadmap-card-b-h" v-if="subitem.subtitle">
          {{ subitem.subtitle }}
        </h2>
        <ul
          class="roadmap-list"
          v-for="(subcontent, index) in subitem.subcontent"
          :key="'subcontent' + index"
        >
          <li style="word-break:break-all">{{ subcontent }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Tabpane",
  props:['items','animated'],
 
};
</script>
