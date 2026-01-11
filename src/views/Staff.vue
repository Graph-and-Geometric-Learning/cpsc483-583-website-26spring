<template>
  <v-container>
    <v-row>
      <v-col>
      <v-sheet class="pa-8" elevation="0">
      <v-card max-width="512px" class="ma-4">
        <v-img :src="rex_ying_image_src" width="512px" height="328px" cover> </v-img>
        <v-card-title>Rex Ying</v-card-title>
        <v-card-subtitle>Instructor</v-card-subtitle>
        <v-card-text>I'm an assistant professor in the Department of Computer Science at Yale University. My research focus includes algorithms for graph neural networks, geometric embeddings, explainable models, and more recently, multi-modal foundation models involving relational reasoning. I am the author of many widely used GNN algorithms such as GraphSAGE, PinSAGE and GNNExplainer. In addition, I have worked on a variety of applications of graph learning in physical simulations, social networks, knowledge graphs, neuroscience and biotechnology. I developed the first billion-scale graph embedding services at Pinterest, and the graph-based anomaly detection algorithm at Amazon.</v-card-text>
      </v-card>
    </v-sheet>
      </v-col>
    </v-row>
    <v-row>
      <v-col v-for="p in staff">
        <PhotoCard v-bind="p" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import PhotoCard from "@/components/PhotoCard.vue";

export default defineComponent({
  components: { PhotoCard },
  data: () => ({
    rex_ying_image_src: new URL(
      "../assets/photos/ying_rex.jpg",
      import.meta.url
    ).href,
    staff: [
      // {
      //     name: "Rex Ying",
      //     image_src: "https://cs.stanford.edu/people/rexy/images/photo_Rex.jpg",
      //     role: "Instructor",
      // },
      {
        name: "Tinglin Huang",
        image_src: new URL("../assets/photos/huang_tinglin.png", import.meta.url)
          .href,
        role: "Head TA",
        bio: "I am a fourth-year Ph.D. student at Computer Science Department. His research interests revolve around computational biology, time-series foundation model and large language models.",
      },
      {
        name: "Hiren Madhu",
        image_src: new URL("../assets/photos/hiren.jpeg", import.meta.url)
          .href,
        role: "TA",
        bio: "I am a second year PhD student at Yale CS.",
      },
      {
        name: "Rishabh Anand",
        image_src: new URL("../assets/photos/anand_rishabh.jpg", import.meta.url)
          .href,
        role: "TA",
        bio: "I am a second-year MS CBB student, previously from Singapore. Research interests include geometric deep learning, generative modelling, drug discovery, and structural biology.",
      },
      {
        name: "Harshit Verma",
        image_src: new URL("../assets/photos/Harshit.jpeg", import.meta.url)
          .href,
        role: "TA",
        bio: "I am a first year MSCS student in the two year track. My research interests include graph learning and time-series foundational models."
      }
    ],
  }),
});
</script>
