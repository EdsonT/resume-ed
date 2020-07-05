<template>
  <v-card color="grey lighten-4" light>
    <v-card-text>
      <content-section title="Who am I?">
        I'm a developer born in Iran and founder of
        <a
          href="http://delix.ir/?utm_source=portiflo&utm_medium=link&utm_content=intro&utm_campaign=delix"
        >Delix.ir</a>,
        <a
          href="https://bytegate.ir/?utm_source=portiflo&utm_medium=link&utm_content=intro&utm_campaign=bytegate"
        >Bytegate.ir</a> and
        <a
          href="http://bobet.ir/?utm_source=portiflo&utm_medium=link&utm_content=intro&utm_campaign=bobet"
        >Bobet.ir</a> and co-founder of
        <a
          href="https://smo.li/?utm_source=portiflo&utm_medium=link&utm_content=intro&utm_campaign=smoli"
        >Smo.li</a>.
        <br />I'm interested and skilled in different topics of Information Technology including programming, web development, and computer and network security.
      </content-section>
      <content-section v-if="myJson.sections.prouds" title="What am I proud of?">
        <v-layout v-for="(proud, i) in myJson.sections.prouds" :key="i">
          <v-flex md1 xs3>
            <v-icon right>{{proud.icon}}</v-icon>
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
            <v-flex v-if="skill.divider" :key="i" md12 xs12 mb-3 />
            <v-flex v-else :key="i" md6 xs12>
              <div class="mr-9 mt-3">
                <div class="align-center">
                  <v-icon small>{{skill.icon}}</v-icon>
                  {{skill.title}}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
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