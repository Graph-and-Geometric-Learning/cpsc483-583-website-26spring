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
    lecture: "Graph Learning Tasks",
  },
  {
    date: "Fri 01/23",
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
    date: "Mon 01/26",
    lecture: "GNN basics",
  },
  {
    date: "Wed 01/28",
    lecture: "GNN Implementations, Objectives and Loss Functions",
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQB8_rk5nJXeRq8E906axcVpAVMwcH1BRTaWK2m20a05OfU?e=8p4Uck",
    readings: [
      {
        title: "Semi-Supervised Classification with GCNs",
        url: "https://arxiv.org/abs/1609.02907",
      },
      {
        title: "Principal Neighbourhood Aggregation for Graph Nets",
        url: "https://arxiv.org/abs/2004.05718",
      },
    ],
    colab: {
      name: "Coding_HW1",
      url: "https://colab.research.google.com/drive/1Wdf8fJZHcmZcZvRx7M9UoCHmn9PknKjj?usp=sharing",
    },
  },
  {
    date: "Mon 02/02",
    lecture: "Training Graph Neural Networks",
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQCCNlExondPRIv6RuS_-FkjAbhZqV6vi7NB9GlwS1OTqjY?e=AXc5TQ",
    readings: [
      {
        title: "Design Space for Graph Neural Networks",
        url: "https://arxiv.org/abs/2011.08843",
      },
      {
        title: "OGB Datasets",
        url: "https://ogb.stanford.edu/docs/nodeprop/",
      },
    ],
  },
  {
    date: "Wed 02/04",
    lecture: "Training Graph Neural Networks",
  },
  {
    date: "Mon 02/09",
    lecture: "Scaling up GNNs",
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQB8VWs-IvAfTpfdHYk77hi_ASrRC3XrxmhzY-wFtTVoPYQ?e=szk5jS",
    readings: [
      {
        title: "GNN Auto Scale",
        url: "https://arxiv.org/abs/2106.05609",
      },
      {
        title: "GraphSAINT",
        url: "https://arxiv.org/abs/1907.04931",
      },
    ],
  },
  {
    date: "Wed 02/11",
    lecture: "GNNs and Transformers",
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQACAUemg5CMRLHl-2YF8PsqAX5h1ow0heoBI6WXRdGVrIs?e=oLcbFN",
    readings: [
      {
        title: "Graph Spectral Theory",
        url: "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQBsS_Qo4zQnTpw0ACx39hbrAYJ_Svl6cw2ttkDA9pPK1hs?e=hGk331",
      },
      {
        title: "Graph Attention Networks",
        url: "https://arxiv.org/abs/1710.10903",
      },
      {
        title: "MultiHop Attention",
        url: "https://arxiv.org/abs/2009.14332",
      },
    ],
    hw: {
      name: "Written-HW2",
      pdf: import.meta.env.BASE_URL + "homework/hw2_CPSC4830.pdf",
    },
    deadline: "Written-HW1 Due",
  },
  {
    date: "Mon 02/16",
    lecture: "GNNs and Transformers",
    deadline: "Coding-HW1 Due",
  },
  {
    date: "Wed 02/18",
    lecture: "Pytorch-Geometric",
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQBUXNxC4QN9TKDU6AfuQ_pjAZRN9VNkcixIqxeLziN56LI?e=08X8yb",
    colab: {
      name: "Coding_HW2",
      url: "https://colab.research.google.com/drive/1IsxfpYdBjqKwhYp4u3lfGP8og05fV_Yh?usp=sharing",
    },
  },
  {
    date: "Mon 02/23",
    lecture: "Theory and Expressive Power of GNNs",
    readings: [
      {
        title: "Graph Isomorphism Network",
        url: "https://arxiv.org/pdf/1810.00826",
      },
    ],
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQD97dcSLBuTS6wJy0lDIWX_AVUi7TyEUMs2DK_nPq7pEJY?e=gqFog7",
    hw: {
      name: "Project Proposal Rubric",
      pdf: import.meta.env.BASE_URL + "homework/Project Proposal - CPSC 4830.pdf",
    },
  },
  {
    date: "Wed 02/25",
    lecture: "Expressive GNNs",
    readings: [
      {
        title: "Identity aware GNNs",
        url: "https://arxiv.org/abs/2101.10320",
      },
      {
        title: "Position-aware GNNs",
        url: "https://arxiv.org/abs/1906.04817",
      },
    ],
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQDrLrkQCGD9T77dPSD1xoIqAW2AElVa0w0I8MU7T3-j7Tk?e=p2erlX",
  },
  {
    date: "Mon 03/02",
    lecture: "Expressive GNNs",
    deadline: "Written-HW2 Due",
  },
  {
    date: "Wed 03/04",
    lecture: "Expressive GNNs",
    deadline: "Coding-HW2 Due",
    hw: {
      name: "Written HW3",
      pdf: import.meta.env.BASE_URL + "homework/hw3.pdf",
    },
  },
  {
    date: "Mon 03/23",
    lecture: "Graph Transformers",
    slide: "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQAJS6lumLC0Q7sX8lJ4LGWAAehSvtyI6hqKBPlHfqBoTP4?e=NDaVZ1",
    readings: [
      {
        title: "Attention is All You Need",
        url: "https://arxiv.org/abs/1706.03762",
      },
      {
        title: "Graph Structure of Neural Networks",
        url: "https://arxiv.org/abs/2007.06559",
      },
    ],
    colab: {
      name: "Colab-HW3",
      url: "https://colab.research.google.com/drive/1t9bGWjhap_J49ASXW39shiOk7WzfnSMh",
    },
  },
  {
    date: "Wed 03/25",
    lecture: "Graph Foundation Models",
    slide:
      "https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQDmgP-yn8WJR6aCy8uVtAbEASc3gSu5dY7e7feS9s7Klvc?e=SRUszP",
    deadline: "Written HW3 due",
  },
  {
    date: "Mon 03/30",
    lecture: "Graph Foundation Models",
  },
  {
    date: "Wed 04/01",
    lecture: "Hyperbolic GNNs",
    slide:"https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQDJS6OGqsZKQpe_9tIz09S0AePfyxqbKReA7NduxEkfL_A?e=FsaZDf",
    readings: [
      {
        title: "HGCNs",
        url: "https://proceedings.neurips.cc/paper/2019/file/0415740eaa4d9decbc8da001d3fd805f-Paper.pdf",
      },
      {
        title: "Hyperbolic GNN Survey",
        url: "https://arxiv.org/abs/2202.13852",
      },
    ],
    hw: {
      name: "Written HW 4",
      pdf: import.meta.env.BASE_URL + "homework/CPSC483_Written_HW4.pdf",
    },
  },
  {
    date: "Mon 04/06",
    lecture: "Geometric Deep Learning",
    slide:"https://yaleedu-my.sharepoint.com/:b:/g/personal/rex_ying_yale_edu/IQA6GYVgW5SZR66ATpQQf1EPAfulKw7mcIxqSQl2zIoYLKA?e=A9scUn",
    deadline: "Colab HW3 Due",
    colab: {
      name: "Colab-HW4",
      url: "https://colab.research.google.com/drive/1xEgJ80zaSdq3qcjpljFQQuZ5zYVcEcAw",
    },
  },
  {
    date: "Wed 04/08",
    lecture: "Geometric Deep Learning",
  },
  {
    date: "Mon 04/13",
    lecture: "Applications in Graphics, Neuroscience and Scientific Simulations",
  },
  {
    date: "Tue 04/14",
    lecture: "Written HW4 Due",
  },
  {
    date: "Tue 04/21",
    lecture: "Colab HW4 Due",
  },
  {
    date: "Mon 04/22",
    lecture: "Final Exam",
  },
  {
    date: "Wed 04/29",
    lecture: "Project Report Due",
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
