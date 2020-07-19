<template>
  <v-app id="r-template">
    <v-fade-transition mode="out-in" type="animation">
      <v-content>
        <div>
          <v-speed-dial v-model="fab" fixed open-on-hover="true" bottom right transition='scale-transition'>
            <template v-slot:activator>
              <v-btn v-model="fab" color="blue-grey" dark fab>
                <v-icon v-if="fab">mdi-close</v-icon>
                <v-icon v-else>mdi-download</v-icon>
              </v-btn>
            </template>
            <v-btn fab dark small color="green">
              <v-icon>mdi-file-pdf</v-icon>
            </v-btn>
            <v-btn fab dark small color="indigo">
              <v-icon>mdi-file-image</v-icon>
            </v-btn>
          </v-speed-dial>
        </div>
        <v-container fluid fill-height>
          <v-layout align-center justify-center>
            <v-flex md10 sm12>
              <v-layout wrap>
                <v-flex md4>
                  <sidebar-container class="fill-height" />
                </v-flex>
                <v-flex md8>
                  <content-container class="fill-height" />
                </v-flex>
              </v-layout>
            </v-flex>
          </v-layout>
        </v-container>
      </v-content>
    </v-fade-transition>
  </v-app>
</template>
<script>
import SidebarContainer from "@/components/sidebar/Container";
import ContentContainer from "@/components/content/Container";
export default {
  name: "ResContainer",
  components: {
    SidebarContainer,
    ContentContainer
  }
};
</script>
<style>
#r-template {
  height: 100%;
  background: #66668d;
  background: -webkit-linear-gradient(to left, #66668d, #4389a2);
  background: linear-gradient(to left, #66668d, #4389a2);
  background-size: cover;
}
</style>