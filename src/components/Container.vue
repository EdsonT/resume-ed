<template>
  <v-app id="r-template">
    <v-fade-transition mode="out-in" type="animation">
      <v-main>
        <div>
          <v-speed-dial
            v-model="fab"
            fixed
            open-on-hover="true"
            bottom
            right
            transition="scale-transition"
          >
            <template v-slot:activator>
              <v-btn v-model="fab" color="blue-grey" dark fab>
                <v-icon v-if="fab">mdi-close</v-icon>
                <v-icon v-else>mdi-download</v-icon>
              </v-btn>
            </template>
            <v-btn fab dark small color="green" @click="downloadPDF">
              <v-icon>mdi-file-pdf</v-icon>
            </v-btn>
            <v-btn fab dark small color="indigo" @click="downloadPNG">
              <v-icon>mdi-file-image</v-icon>
            </v-btn>
          </v-speed-dial>
        </div>
        <div ref="capture">
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
                <v-layout>
                  <v-flex md12>
                    <timeline />
                  </v-flex>
                </v-layout>
              </v-flex>
            </v-layout>
          </v-container>
        </div>
      </v-main>
    </v-fade-transition>
  </v-app>
</template>
<script>
import SidebarContainer from "@/components/sidebar/Container";
import ContentContainer from "@/components/content/Container";
import Timeline from "@/components/timeline/Container";
import saveAs from "file-saver";
import jsPDF from "jspdf";
import html2canvas from "html2canvas";
export default {
  name: "ResContainer",
  components: {
    SidebarContainer,
    ContentContainer,
    Timeline,
  },
  methods: {
    downloadText() {
      let pdfName = "test";
      const doc = new jsPDF();
      const contentHtml = this.$refs.content.innerHTML;
      doc.fromHTML(contentHtml, 15, 15, {
        width: 170,
      });
      doc.save(pdfName + ".pdf");
    },
    downloadPDF() {
      const doc = new jsPDF();
      var canvasElement = document.createElement("canvas");
      html2canvas(this.$refs.content, {
        scale: "7",
        canvas: canvasElement,
      }).then(function (canvas) {
        const img = canvas.toDataURL("image/jpeg", 0.8);
        doc.addImage(img, "JPEG", 0, 0, 250, 150);
        doc.save("sample.pdf");
      });
    },
    showCaptureRef() {
      console.log(this.$refs.capture);
    },
    downloadPNG() {
      // let vc = this;

      let filename = "Report.png";
      html2canvas(this.$refs.capture, { scale: "6" })
        .then((canvas) => {
          saveAs(canvas.toDataURL("png", 0.8), filename);
        })
        .catch((error) => {
          alert(error);
        });
    },
  },
};
</script>
<style>
#r-template {
  height: 100%;
  background-image: linear-gradient(to right, #d7d2cc 0%, #304352 100%);
  background-size: cover;
}
</style>
