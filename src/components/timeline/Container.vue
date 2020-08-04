<template>
  <v-card color="grey lighten-4" light>
    <v-card-text>
      <content-section id="timeline" title="My Experiences">
        <v-timeline dense>
          <v-timeline-item v-for="(item,i) in myJson.timeline.items" :key="i" large>
            <template v-slot:icon>
              <v-avatar>
                <img src="http://i.pravatar.cc/64" />
              </v-avatar>
            </template>
            <v-card class="elevation-3" shaped>
              <v-card-title class="headline">
                <span class="mb-1">
                  {{item.title}}
                  <span class="blue-grey--text lighten-1">at&nbsp;{{item.employeer}}</span>
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