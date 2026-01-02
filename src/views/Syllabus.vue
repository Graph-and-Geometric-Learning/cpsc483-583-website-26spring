<template>
  <v-container>
    <v-row>
      <v-col>
        <v-table>
          <thead>
            <tr>
              <th>Date</th>
              <th>Lecture</th>
              <th>Slides</th>
              <th>Recording</th>
              <th>Readings</th>
              <th>Assignment</th>
              <th>Deadlines</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in items">
              <td>{{ item.date }}</td>
              <td>
                {{ item.lecture }}
                <a v-if="item.date === 'Mon 10/02'" href="https://yale.zoom.us/j/94207787464?from=addon">[Zoom]</a>
              </td>
              <td><a v-if="item.slide" :href="item.slide">[slides]</a></td>
              <td><a v-if="item.recording" :href="item.recording">[recording]</a></td>
              <td>{{ item.reading }}</td>
              <td>
              <div v-if="item.hw">
                {{ item.hw.name }} released <a :href="item.hw.pdf">[pdf]</a> <a :href="item.hw.zip">[zip]</a>
              </div>
              <br v-if="item.colab" />
              <div v-if="item.colab">
              <a target="_blank" :href="item.colab.url">
                <img src="https://colab.research.google.com/assets/colab-badge.svg" :alt="item.colab.name" />
              </a>
                <!-- {{ item.colab.name }} released <a :href="item.colab.url">[ipynb]</a> -->
              </div>

              </td>
              <td>{{ item.deadline }}</td>
            </tr>
          </tbody>
        </v-table>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import HelloWorld from "@/components/HelloWorld.vue";
import { defineComponent } from "vue";

interface HW {
  name: string,
  pdf: string,
  zip: string,
}

interface Colab {
  name: string,
  url: string,
}

interface Item {
  date: string;
  lecture: string;
  slide?: string;
  reading?: string;
  event?: string;
  deadline?: string;
  hw?: HW;
  colab?: Colab;
  recording?: string;
}

enum EventType {
  homework,
  colab,
}

var items: Item[] = [
  {
    "date": "Wed 01/14",
    "lecture": "Introduction",
    slide: "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/EYJG3bz_K9NKlTVN4dUEDvwBvkR_Zr70aSTumbze55AdRA",
  },
  {
    "date": "Fri 01/16",
    "lecture": "Graph Learning Tasks",
  },
  {
    "date": "Wed 01/21",
    "lecture": "Deep Learning Background and GNN basics",
  },
  {
    "date": "Fri 01/23",
    "lecture": "No classes",
  },
  {
    "date": "Wed 01/28",
    "lecture": "GNN Implementations, Objectives and Loss Functions",
  },
  {
    "date": "Fri 01/30",
    "lecture": "Scalable GNN Architectures",
  },
  {
    "date": "Wed 02/04",
    "lecture": "Graph Attention Networks and Heterogeneous graphs",
  },
  {
    "date": "Fri 02/06",
    "lecture": "GNNs and Transformers",
  },
  {
    "date": "Wed 02/11",
    "lecture": "Theory of Graph Neural Networks",
  },
  {
    "date": "Fri 02/13",
    "lecture": "Guest Lecture 1",
  },
  {
    date: "Wed 02/18",
    "lecture": "GNN Expressive Power",
  },
  {
    "date": "Fri 02/20",
    "lecture": "GNN Expressive Power (2)",
  },
  {
    "date": "Wed 02/25",
    "lecture": "Graph Learning Tools"
  },
  {
    "date": "Fri 02/27",
    "lecture":  "Graph Transformers",
  },
  {
    "date": "Wed 03/04",
    "lecture": "Self-supervised Learning with GNNs",
  },
  {
    "date": "Fri 03/06",
    "lecture": "No classes",
  },
  {
    "date": "Wed 03/25",
    "lecture": "Self-supervised Learning with GNNs (2)",
  },
  {
    "date": "Fri 03/27",
    "lecture": "Hyperbolic Embeddings and Hyperbolic GNNs",
  },
  {
    "date": "Wed 04/01",
    "lecture": "Distributed Node Embeddings",
  },
  {
    "date": "Fri 04/03",
    "lecture": "Graph Generative Models",
  },
  {
    "date": "Wed 04/08",
    "lecture": "Knowledge Graph Embeddings",
  },
  {
    "date": "Fri 04/10",
    "lecture": "XAI for Graphs",
  },
  {
    "date": "Wed 04/15",
    "lecture": "Multimodal Graph Learning"
  },
  {
    date: "Fri 04/17",
    "lecture": "Applications in Graphics, Neuroscience and Scientific Simulations",
  }
];

export default defineComponent({
  name: "Syllabus",

  data: () => ({
    items: items,
  }),
  methods: {
    baseName(str) {
      var base = new String(str).substring(str.lastIndexOf("/") + 1);
      if (base.lastIndexOf(".") != -1)
        base = base.substring(0, base.lastIndexOf("."));
      return base;
    },
  },
});
</script>
