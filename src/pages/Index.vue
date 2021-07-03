<template>
  <Layout>
    <div class="container">
      <Hero />
      <ProjectsGrid :projects="$page.project.edges" />
    </div>
    <LatestJournals :journals="$page.journal.edges" />
  </Layout>
</template>

<page-query>
query {
	project: allStrapiProject {
    edges {
      node {
        id
        date (format: "YYYY")
        title
        categories
        thumbnail {
          url
        }
        path
      }
    }
  },
  journal: allStrapiJournalPost (perPage: 4) {
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
  }
}
</script>