<template>
  <section>
    <hr>
    <h2>Projects</h2>
    <div
      class="project"
      v-for="project in projects"
      :key="project.id"
    >
      <h3><a :href="project.source">{{ project.name }}
          <font-awesome-icon :icon="['fas', 'external-link-alt']" /></a></h3>
      <p>{{ project.description }} <em>({{ project.start }})</em></p>
      <figure v-if="project.demo">
        <!-- <a :href="'assets/project_previews/' + project.preview_url"><img
            :src="'assets/project_previews/' + project.preview_url"
            :alt="project.name + 'Demo Image'"
          ></a> -->
        <figcaption><a
            :href="project.demo"
            v-if="project.demo !== ''"
          >Demo</a>
          <div v-else>Demo not available</div>
          <!-- | <a :href="project.website">Website</a> -->
        </figcaption>
      </figure>
    </div>
    <!-- Printer friendly Project Section -->
    <ul
      class="project--printer-friendly"
      v-for="project in projects"
      :key="project.id"
    >
      <li>
        <p><strong>{{ project.name }}</strong> ({{ project.start }}) - {{ project.description }}</p>
        <p>Source: <a :href="project.source">{{ project.source }}</a></p>
      </li>
    </ul>
  </section>
</template>
<script>
export default {
  name: 'ProjectSection',
  props: ['projects']
}
</script>
<style scoped>
h3 a {
  text-decoration: none;
  color: black;
}
img {
  width: auto;
  height: auto;
  max-height: 25vh;
  max-width: 55vh;
  margin: 1rem;
}
.project {
  display: flex;
  flex-direction: column;
  margin-top: 1rem;
  margin-bottom: 2rem;
}
.project--printer-friendly {
  display: none;
}
@media screen and (max-width: 600px) {
  figure {
    text-align: center;
    margin: 0;
  }
  img {
    max-width: 40vh;
  }
}
@media print {
  p,
  a {
    margin: 0;
  }
  .project {
    display: none;
  }
  .project--printer-friendly {
    display: block;
  }
}
</style>