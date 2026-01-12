<template>
    <v-container>
        <v-row>
            <v-col>
                <v-sheet class="pa-8" elevation="6">
                    <h1>Grading</h1>

                    <ul>
                        <li><b>Homework</b>: 30%
                            <ul>
                                <li>Homework 1, 2, 3, each worth 10%</li>
                            </ul>
                        </li>
                        <li><b>Coding assignment: 20%</b>
                            <ul>
                                <li>4 (short) coding assignments using Google Colab / Jupyter Notebook</li>
                            </ul>
                        </li>
                        <li><b>Exam (during the last lecture): 20%</b>
                            <ul>
                                <li>Light-weight 1 hour exam (closed book).</li>
                            </ul>
                        </li>
                        <li><b>Course Project</b>: 30%
                            <ul>
                                <li>Proposal: 30%
                                </li>
                                <li> Final report: 70%
                                </li>
                            </ul>
                        </li>
                        <li><b>Extra Credit: code contribution</b>: up to 10%
                            <ul>
                                <li>Opensource contributions: PyG, new library / public benchmarks related to the course
                                </li>
                                <li>Used if you are on the boundary between grades</li>
                            </ul>
                        </li>
                    </ul>
                </v-sheet>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <v-sheet class="pa-8" elevation="6">
                    <h1>Homework</h1>
                    <ul>
                        <li>Assignments take time. <b>Start early!</b>
                            <ul>
                                <li>A combination of data analysis, algorithm design and math.</li>
                            </ul>
                        </li>
                        <li>How to submit?
                            <ul>
                                <li><a href="https://yale.instructure.com/courses/114025">Canvas</a></li>
                                <li>Both homework (including code) and project deliverables (pdf) must be uploaded</li>
                                <li>We prefer <em>LaTeX</em> submissions</li>
                                <li>If you really need to use hand-writing, make sure it's readable. TAs have no
                                    obligations to use magnifying glasses to figure out what you write.</li>
                            </ul>
                        </li>
                        <li>Total of 2 <em>Late Periods</em> (LP) per student (up to 5 working days)
                            <ul>
                                <li>Max 1 late period per written or coding assignment (no LP for final report)</li>
                            </ul>
                        </li>
                    </ul>
                </v-sheet>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <v-sheet class="pa-8" elevation="6">
                    <h1>Honor Code</h1>
                    We strictly enforce the <a
                        href="https://academiccontinuity.yale.edu/academic-integrity-honor-codes">Yale Honor Code</a>.
                    Violations of the Honor Code include
                    <ul>
                        <li>Copying or allowing another to copy from one's own paper</li>
                        <li>Unpermitted collaboration</li>
                        <li><a
                                href="https://poorvucenter.yale.edu/undergraduates/using-sources/understanding-and-avoiding-plagiarism/what-plagiarism">Plagiarism</a>
                        </li>
                        <li>Giving or receiving unpermitted aid on an examination
                        </li>
                        <li>Representing as one’s own work the work of another
                        </li>
                        <li>Giving or receiving aid on an assignment under circumstances in which a reasonable person
                            should have known that such aid was not permitted
                        </li>
                    </ul>
                    The <a href="https://bulletin.yale.edu/bulletins/som/rights-and-responsibilities-students">sanction</a>
                    for
                    even a first offense is severe.
                </v-sheet>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <v-sheet class="pa-8" elevation="6">
                    <h1>Projects</h1>
                    <ul>
                        <li><b>Due Date</b>
                            <ul>
                                <li>Final Project report is due on the last day of classes</li>
                                <li>Note: Late days do not apply to the proposal and report. There will be no extensions
                                    granted for either.</li>
                            </ul>
                        </li>
                        <li><b>Project Group Formation</b>
                            <ul>
                                <li>Individual project is recommended. You may also form groups of up to 2 students. Team
                                    size will be taken under consideration when evaluating the scope of the project in
                                    breadth and depth.</li>
                            </ul>
                        </li>
                        <li>
                            <b>Grading</b>
                            <ul>
                                <li>Generally, grading will be the same for all project members except in some cases of
                                    unequal contribution.</li>
                            </ul>
                        </li>
                    </ul>
                    <h1 class="my-4">Project Proposals</h1>
                    <ol class="ml-4">
  <li>
    <strong>Research Problem Definition (10pts):</strong>
    <p>
      Define the problem that you will be investigating in this project. Consider addressing the following:
      <ul>
        <li>What makes this problem interesting to you?</li>
        <li>What is your deep learning algorithm trying to learn?</li>
        <li>Why is the selected topic important?</li>
        <li>What is the overall goal of your project?</li>
      </ul>
    </p>
  </li>
  
  <li>
    <strong>Dataset (20pts):</strong>
    <p>
    Which dataset will you use? 
    Provide a detailed description of the dataset you plan to use for this project.  
    Include some preliminary analysis of your dataset, such as graph statistics (graph size and degree distribution), or other relevant characteristics. 
    Whenever possible, include visualizations in your proposal to help clarify and enhance our (and yourself) understanding of your dataset.
    </p>
  </li>

  <li>
    <strong>Description of Related Works (20pts):</strong>
    <p>
    Conduct a comprehensive literature review regarding your project e.g., If you want to propose a new GNN algorithm, review similar algorithms; if your goal is to apply an algorithm to a new domain, examine how similar approaches have been adapted in other domains). Be sure to clearly explain how your work relates to and builds upon the existing research i.e., explain the similarities and differences). 
    </p>
  </li>

  <li>
    <strong>Proposed Approaches (30pts):</strong>
    <p>
    Which approaches/algorithms will you use? 
Each team member (if applicable) should implement their own proposed approach. While methods may have shared elements, they should have unique elements. 
Each team member should write up their own subsection detailing the methodology they will implement individually (e.g., Section 2.1 Proposed Methodology 1 (Chuhan)). </p><p>
<strong>Note</strong>: Be aware if you are replicating or using existing repositories/code, please propose a non-trivial adjustment, such as evaluating the model on a new dataset or adjusting a component of the model architecture or loss. 
Alternatively, one may combine two repositories for a novel application. 
<ul>
    <li>
    <strong>Research Questions and hypothesis</strong>
    <p>    Briefly describe your research questions and hypothesis. 
    These questions should be more detailed than the general research questions outlined in item 1. 
    For instance, if your overall research question is to propose a new clustering algorithm, your specific research questions could be <i>what's the performance difference between my clustering algorithm and heuristic clustering algorithms, such as k-means, dbscan, and mean shift?</i> Your hypothesis could be <i>my proposed algorithm will run faster than any of these heuristics, while maintaining high accuracy.</i> </p>
    </li>
</ul>
    </p>
  </li>

  <li>
    <strong>Evaluation Metrics and Expected Results (10pts):</strong>
    <p>
    What evaluation metrics will you use to evaluate your result?
Consider your research questions — what are the expected results that will help answer these questions?
Ensure that the metrics and expected results align with your research objectives and demonstrate the effectiveness of your approach.
</p> 
 </li>

  <li>
    <strong>Timeline (10pts):</strong>
    <p>
    Provide a detailed project timeline for the semester, outlining key milestones and deadlines. 
Additionally, specify how tasks will be divided among team members (if applicable) to ensure efficient progress.
    </p>
  </li>
</ol>
<h1>Excellent Project Reports</h1>
    <ul>
        <li v-for="(project, index) in projects" :key="index">
            <a :href="project.link">[{{ project.name }}]</a>
        </li>
    </ul>

                </v-sheet>
            </v-col>
        </v-row>
    </v-container>
</template>

<script setup>
let projects = [
    {
        name: "Tristan Brigham",
        link: import.meta.env.BASE_URL + "reports/" + "brigham.pdf",
    },
    {
        name: "Andreas Varvarigos",
        link: import.meta.env.BASE_URL + "reports/" + "varvarigos.pdf",
    },
    {
        name: "Ananya Krishna & Arjan kohli",
        link: import.meta.env.BASE_URL + "reports/" + "arjan.pdf",
    },
    {
        name: "Lucas lee",
        link: import.meta.env.BASE_URL + "reports/" + "lee.pdf",
    },
]
</script>
