<template>
  <v-card color="grey lighten-4" light>
    <v-card-text>
      <content-section id="timeline" title="My Experiences">
        <v-timeline dense>
          <v-timeline-item v-for="(item,i) in myJson.timeline.items"  :key="i" large :icon="item.icon ||''" fill-dot  icon-color="blue-grey darken-4"  color="blue-grey lighten-5">
            <template v-if="item.iconImage" v-slot:icon >
              <v-avatar>
                <img :src="item.iconImage" />
              </v-avatar>
            </template>
            <v-card class="elevation-3" shaped>
              <v-card-title class="headline">
                <span class="mb-1">
                  {{item.title}}
                  <span >at&nbsp;</span>
                  <span class="light-blue--text text--darken-4">{{item.employeer}}</span>
                </span>
              </v-card-title>
              <v-card-subtitle>{{item.from}} - {{item.to}}</v-card-subtitle>
              <v-card-text>
                <span v-html="item.html"></span>
              </v-card-text>
            </v-card>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>
<script>
import ContentSection from "@/components/content/Section";
import json from "@/external/data.json";
export default {
  name: "Timeline",
  components: { ContentSection },
  data() {
    return {
      myJson: json,
    };
  },
};
</script>
<style scoped>
title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent {
  opacity: 0.6;
}
</style>