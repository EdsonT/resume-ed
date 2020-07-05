<template>
  <v-card color="grey darken-3" dark>
    <v-card-text>
      <avatar />
      <div class="text-sm-center mb-4 mt-3">
        <h1 class="mb-1">
          Edson
          <span class="light-blue--text text--lighten-3">Tarqui</span>
        </h1>
        <span >Technical Product Manager</span>
      </div>
      <sidebar-section :options="myjson.sections.info" />
      <sidebar-section :options="myjson.sections.socials" />
      <sidebar-section :options="myjson.sections.hobbies">
        <template v-slot:item="{item}">
          
          <v-chip class="ma-1" input-value="false">
            <v-avatar left>
              <v-icon>{{item.icon}}</v-icon>
            </v-avatar>
            {{item.text}}
          </v-chip>
          
        </template>
      </sidebar-section>
      <sidebar-section :options="myjson.sections.languages">
        <template v-slot:items="{items}">
          <v-container pa-0>
            <v-layout wrap class="text-xs-center">
              <template v-for="(item,i) in items">
                <v-flex :key="i" md3 sm4 xs6>
                  <v-progress-circular
                    rotate="360"
                    size="65"
                    width="2"
                    :value="item.value"
                    color="white"
                    class="ma-2"
                  >{{item.text}}</v-progress-circular>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>
<script>
import Avatar from "@/components/sidebar/Avatar";
import SidebarSection from "@/components/sidebar/Section";
import json from "@/external/data.json";

export default {
  data() {
    return {
      myjson: json
    };
  },
  name: "Sidebar",
  components: {
    Avatar,
    SidebarSection
  }
};
</script>
<style scoped>
.sidebar {
  background: #2e2e2e;
}
</style>