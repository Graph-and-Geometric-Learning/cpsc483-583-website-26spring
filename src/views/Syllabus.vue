<template>
  <v-container>
    <v-row>
      <v-col>
        <v-table style="table-layout: auto; width: 100%;">
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
            <tr v-for="item in items" :key="item.date + item.lecture">
              <td>{{ item.date }}</td>

              <td>
                {{ item.lecture }}
                <a
                  v-if="item.date === 'Mon 10/02'"
                  href="https://yale.zoom.us/j/94207787464?from=addon"
                  target="_blank"
                  rel="noopener"
                >
                  [Zoom]
                </a>
              </td>

              <td>
                <a v-if="item.slide" :href="item.slide" target="_blank" rel="noopener">[slides]</a>
              </td>

              <td>
                <a v-if="item.recording" :href="item.recording" target="_blank" rel="noopener">[recording]</a>
              </td>

              <td class="py-2 overflow-visible" style="white-space: normal; height: auto;">
                <div v-if="item.readings?.length" style="display: flex; flex-direction: column; gap: 4px;">
                  <a
                    v-for="r in item.readings"
                    :key="r.url"
                    :href="r.url"
                    target="_blank"
                    rel="noopener"
                  >
                    {{ r.title }}
                  </a>
                </div>
              </td>

              <td class="py-2 overflow-visible" style="white-space: normal; height: auto; overflow: visible;">
                <div v-if="item.hw">
                  {{ item.hw.name }} released
                  <a :href="item.hw.pdf" target="_blank" rel="noopener">[pdf]</a>
                  <a v-if="item.hw.zip" :href="item.hw.zip" target="_blank" rel="noopener">[zip]</a>
                </div>

                <div
                  v-if="item.colab"
                  style="display: flex; align-items: center; gap: 8px; flex-wrap: wrap; overflow-wrap: anywhere;"
                >
                  <a target="_blank" rel="noopener" :href="item.colab.url">
                    <img
                      src="https://colab.research.google.com/assets/colab-badge.svg"
                      :alt="item.colab.name"
                      :title="item.colab.name"
                      style="vertical-align: middle;"
                    />
                  </a>

                  <a
                    target="_blank"
                    rel="noopener"
                    :href="item.colab.url"
                    style="overflow-wrap: anywhere;"
                  >
                    {{ item.colab.name }}
                  </a>
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
import { defineComponent } from "vue";

interface HW {
  name: string;
  pdf: string;
  zip?: string;
}

interface Colab {
  name: string;
  url: string;
}

interface Readings {
  title: string;
  url: string;
}

interface Item {
  date: string;
  lecture: string;
  slide?: string;
  readings?: Readings[];
  deadline?: string;
  hw?: HW;
  colab?: Colab;
  recording?: string;
}

const items: Item[] = [
  {
    date: "Mon 01/12",
    lecture: "Introduction",
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQBU_0Zbj1NaSK2NI_M_2F2eAVMF-8xNw-AbOG_JgdMv8hI?e=oNeQhd",
  },
  {
    date: "Wed 01/14",
    lecture: "Graph Learning Tasks",
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQCiDNGR2Yq_TLONYEfm93ifAbpSucD7NPjiY3NEshulWpU?e=xuFhgD",
    readings: [
      {
        title: "Graphlet-Decomposition",
        url: "https://arxiv.org/abs/1506.04322",
      },
      {
        title: "PageRank",
        url: "https://patents.google.com/patent/US7058628B1/en",
      },
    ],
    hw: {
      name: "Written_HW1",
      pdf: import.meta.env.BASE_URL + "homework/hw1_CPSC4830.pdf",
    },
  },
  {
    date: "Mon 01/19",
    lecture: "No classes (MLK Day)",
  },
  {
    date: "Wed 01/21",
    lecture: "GNN basics",
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQDr03ACHseaQLBsJNuKcdkZAWNqpIujYYj-VNO_VlxM47k?e=l1eKMN",
    readings: [
      {
        title: "Representation Learning on Graphs",
        url: "https://arxiv.org/pdf/1709.05584",
      },
      {
        title: "GraphSAGE",
        url: "https://arxiv.org/abs/1706.02216",
      },
    ],
  },
  {
    date: "Fri 01/23",
    lecture: "GNN Implementations, Objectives and Loss Functions",
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQB8_rk5nJXeRq8E906axcVpAVMwcH1BRTaWK2m20a05OfU?e=8p4Uck",
    colab: {
      name: "Coding_HW1",
      url: "https://colab.research.google.com/drive/1Wdf8fJZHcmZcZvRx7M9UoCHmn9PknKjj?usp=sharing",
    },
  },
  {
    date: "Mon 01/26",
    lecture: "Scalable GNN Architectures",
  },
  {
    date: "Wed 01/28",
    lecture: "Graph Attention Networks and Heterogeneous graphs",
  },
  {
    date: "Mon 02/02",
    lecture: "GNNs and Transformers",
  },
  {
    date: "Wed 02/04",
    lecture: "Theory of Graph Neural Networks",
  },
  {
    date: "Mon 02/09",
    lecture: "Guest Lecture 1",
    deadline: "Written-HW1 Due",
  },
  {
    date: "Wed 02/11",
    lecture: "GNN Expressive Power",
  },
  {
    date: "Mon 02/16",
    lecture: "GNN Expressive Power (2)",
    deadline: "Coding-HW1 Due",
  },
  {
    date: "Wed 02/18",
    lecture: "Graph Learning Tools - Hands-on Session",
  },
  {
    date: "Mon 02/23",
    lecture: "Graph Transformers",
  },
  {
    date: "Wed 02/25",
    lecture: "Graph Foundation Models",
  },
  {
    date: "Mon 03/02",
    lecture: "Guest Lecture 2",
  },
  {
    date: "Wed 03/04",
    lecture: "Hyperbolic Embeddings and Hyperbolic GNNs (1)",
  },
  {
    date: "Wed 03/25",
    lecture: "Hyperbolic Embeddings and Hyperbolic GNNs (2)",
  },
  {
    date: "Mon 03/30",
    lecture: "Graph Generative Models",
  },
  {
    date: "Wed 04/01",
    lecture: "Knowledge Graph Embeddings",
  },
  {
    date: "Mon 04/06",
    lecture: "XAI for Graphs",
  },
  {
    date: "Wed 04/08",
    lecture: "Geometric Equivariant GNNs",
  },
  {
    date: "Mon 04/13",
    lecture: "Applications in Graphics, Neuroscience and Scientific Simulations",
  },
];

export default defineComponent({
  name: "Syllabus",
  data: () => ({
    items,
  }),
  methods: {
    baseName(str: string) {
      let base = str.substring(str.lastIndexOf("/") + 1);
      if (base.lastIndexOf(".") !== -1) base = base.substring(0, base.lastIndexOf("."));
      return base;
    },
  },
});
</script>
