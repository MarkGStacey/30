<template>
  <Layout>
    <div class="container">
      <!-- <button @click="imgSrc = '/assets/static/uploads/card (' + Math.floor(Math.random() * 58) + ').jpeg?width=800&quality=90&fit=cover&key=51a209a'">New card</button> -->
      <!-- <Hero />
      <ProjectsGrid :projects="$page.projects.edges" /> -->
    </div>
    <!-- {{imgSrc}} -->
    <g-image :src="imgSrc"></g-image>
    <!-- <g-image src="/assets/static/uploads/card (1).jpeg?width=800&quality=90&fit=cover&key=51a209a"></g-image> -->
    
    <!-- <LatestJournals :journals="$page.journals.edges" /> -->
  </Layout>
</template>

<page-query>
query Posts {
	projects: allProjectPost {
    edges {
      node {
        id
        date (format: "YYYY")
        title
        categories
        thumbnail (quality: 90)
        path
      }
    }
  },
  journals: allJournalPost (perPage: 4) {
    edges {
      node {
        id
        path
        title
      }
    }
  }
}
</page-query>

<script>
import Hero from "@/components/Hero"
import ProjectsGrid from "@/components/ProjectsGrid"
import LatestJournals from "@/components/LatestJournals"

export default {
  components: {
    Hero,
    ProjectsGrid,
    LatestJournals
  },
  data() {
    return {
        imgSrc: '/assets/static/uploads/card (' + Math.floor(Math.random() * 58) + ').jpeg?width=800&quality=90&fit=cover&key=51a209a'
    }
  }
}
</script>
