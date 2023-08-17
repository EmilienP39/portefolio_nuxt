<template>
  <div id="projects" class="project">
    <h2>Projects</h2>
    <p>I show you to all the big and small websites I have done so far</p>
    <div class="projects-box">
      <div class="proj-imgbx" v-for="project in this.projects" @click="this.focusProject(project)" :class="isFocusVisible && this.projectFocus.id === project.id ? 'animation' : 'info-project'">
        <img src="assets/MSI.png"/>
        <div class="proj-txtx">
          <h4>{{project.nom}}</h4>
          <span>{{project.description}}</span>
        </div>
        <div class="proj-imgbx">
          <img :src="project.image"/>
        </div>
      </div>
    </div>
  </div>
  <img class="background-image-right" src="assets/color-sharp2.png" alt="Image"/>
  <div style="background: #000;position: fixed; opacity: 0.5; z-index: 10;inset: 0" v-if="isFocusVisible" @click="this.isFocusVisible = false;"> </div>
</template>

<script lang="ts">

import  {Project} from "~/Interfaces/Project";

export default defineComponent({
  name:'Project',
  data() {
    return {
      projects: [
        {
          id:1,
          nom:"MSI",
          description:"MSI est un outil de gestion de ticket interne fait avec VueJS typescript et Symfony. Chaque ticket est créé automatiquement à partir des mails que l'on reçoit.",
          image:"assets/MSI.png"
        } as Project,
        {
          id:2,
          nom:"TEST",
          description: "fdsfdsfs",
          image:"assets/MSI.png"
        } as Project
      ] as Project[],
      projectFocus: {} as Project,
      isFocusVisible: false as Boolean
    }
  },
  methods: {
    focusProject(project: Project){
      if(this.isFocusVisible){
        this.isFocusVisible = false;
      }else{
        this.isFocusVisible = true;
      }
      this.projectFocus = project;
    }
  }
})
</script>

<style>
project {
  padding: 80px 0;
  position: relative;
  background-color: black;
}
.project h2 {
  font-size: 45px;
  font-weight: 700;
  text-align: center;
}
.project p {
  color: #B8B8B8;
  font-size: 18px;
  letter-spacing: 0.8px;
  line-height: 1.5em;
  margin: 14px auto 30px auto;
  text-align: center;
  width: 56%;
}
.projects-box{
  display: flex;
  flex-direction: row;
  margin: 0 15em;
  flex-wrap: wrap;
  justify-content: left;

}
.proj-imgbx {
  position: relative;
  border-radius: 30px;
  overflow: hidden;
  max-width: 415px;
  max-height: 200px;
  margin: 24px;
  transition: transform .2s ease-out;
  cursor:pointer;
}
.info-project::before {
  content: "";
  background: linear-gradient(90.21deg, #AA367C -5.91%, #4A2FBD 111.58%);
  opacity: 0.85;
  position: absolute;
  width: 100%;
  height: 0;
  transition: 0.4s ease-in-out;
}
.info-project:hover::before {
  height: 100%;
}
.proj-txtx {
  position: absolute;
  text-align: center;
  top: 65%;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: 0.5s ease-in-out;
  opacity: 0;
  width: 100%;
}
.info-project:hover .proj-txtx {
  top: 50%;
  opacity: 1;
}
.proj-txtx h4 {
  font-size: 30px;
  font-weight: 700;
  letter-spacing: 0.8px;
  line-height: 1.1em;
}
.proj-txtx span {
  font-style: italic;
  font-weight: 400;
  font-size: 15px;
  letter-spacing: 0.8px;
}
.background-image-right {
  top: 80%;
  position: absolute;
  bottom: 0;
  width: 35%;
  right: 0;
  z-index: -4;
}
.animation{
  position: fixed;
  top: 50%;
  left: 50%;
  margin-top: -9em;
  margin-left: -15em;
  transform:scale(3.5);
  z-index :11;
  border-radius: 0;
}
</style>