<template>
  <div class="home">
    <b-container>
      <b-row align-v="center">
        <JobCard
          v-for="job in displayJobs"
          :key="job.id"
          :name="job.title"
        ></JobCard>
      </b-row>
      <b-pagination
        class="mb-5"
        align="center"
        v-model="currentPage"
        :total-rows="rows"
        :per-page="perPage"
        first-text="First"
        prev-text="Prev"
        next-text="Next"
        last-text="Last"
        @input="paginate(currentPage)"
      ></b-pagination>
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
import JobCard from "@/components/JobCard.vue";
import { mapGetters } from "vuex";

export default {
  name: "Home",
  components: { JobCard },
  computed: {
    ...mapGetters(["jobs", "rows", "displayJobs"]),
  },
  data() {
    return {
      // displayJobs: [],
      currentPage: 1,
      perPage: 3,
      // rows: 1,
    };
  },
  mounted() {
    this.fetchData();
  },

  methods: {
    async fetchData() {
      await this.$store.dispatch("fetchJobs");
      // console.log("test", this.$store.getters.jobs);
      // const res = await fetch("dump.json");
      // const val = await res.json();
      // this.jobs = jobs;
      // this.rows = this.jobs.length;
      this.paginate();
    },

    paginate(currentPage) {
      this.$store.dispatch("paginate", { currentPage, perPage: this.perPage });
      // const start = (currentPage - 1) * this.perPage;
      // this.displayJobs = this.jobs.slice(start, start + 3);
    },
  },
};
</script>
