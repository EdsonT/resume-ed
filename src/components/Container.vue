<template>
  <v-app id="r-template">
    <v-fade-transition mode="out-in" type="animation">
      <v-content>
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