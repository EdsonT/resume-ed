<template>
  <v-card color="grey lighten-4" light>
    <v-card-text>
      <content-section :title="myJson.intro.title">
        {{myJson.intro.text}}
      </content-section>
      <content-section v-if="myJson.sections.prouds" title="What am I proud of?">
        <v-layout v-for="(proud, i) in myJson.sections.prouds" :key="i">
          <v-flex md1 xs3>
            <v-icon color="blue-grey" right>{{proud.icon}}</v-icon>
          </v-flex>
          <v-flex md11 xs9>
            <p>
              <strong>{{proud.text}}</strong>
              <br />
              <small>{{proud.source}}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section v-if="myJson.sections.educations" title="Education">
        <v-layout v-for="(education,i) in myJson.sections.educations" :key="i">
          <v-flex md4>{{education.from}} - {{education.to}}</v-flex>
          <v-flex>
            <strong v-if="education.title">{{education.title}}</strong>
            <div v-if="education.location">
              <i>{{education.location}}</i>
            </div>
            <div v-if="education.description">{{education.description}}</div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section v-if="myJson.sections.skills" id="to-timeline" title="Skills and Expertize">
        <!-- <template slot="actions">(% are relative not absolute)</template> -->
        <v-layout wrap>
          <template v-for="(skill,i) in myJson.sections.skills">
            <v-flex v-if="skill.divider" :key="i" />
            <v-flex v-else :key="i" md6 xs12>
              <div class="mr-4 mt-4">
                <div class="align-center">
                  <v-icon small color="blue-grey darken-1">{{skill.icon}}</v-icon>
                  {{skill.title}}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="5"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>
<script>
import ContentSection from "@/components/content/Section";
import json from "@/external/data.json";
export default {
  data() {
    return {
      myJson: json
    };
  },
  name: "MainContent",
  components: { ContentSection }
};
</script>
<style scoped>
.title {
  border-bottom: 2px #bfbfbf sold;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>