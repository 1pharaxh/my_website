<template>
          <div style="text-align:center; padding-top: 15%;">
    <!-- <cursor-fx  color='#1DE9B6' color-hover='#FF8A65'/> -->
    <h1 class="mainheader">
        <p class="contain"><span class="prima" data-cursor-hover>My<span class="seconda" data-cursor-hover>Experience...</span></span><span class="centered">EXPERIENCE</span></p>
    </h1>
    <v-divider></v-divider>
    <div class="divWidth">
    <v-timeline v-if="isRenderTimeline1" >
      <v-timeline-item
        v-for="(year, i) in years"
        :key="i"
        :color="year.color"
        small
      >
        <template v-slot:opposite>
          <span
            :class="`headline font-weight-bold ${year.color}--text`"
            v-text="year.year"
          ></span>
        </template>
        <div class="py-4">
          <h2 :class="`headline font-weight-light mb-4 ${year.color}--text`" data-cursor-hover>
            {{year.title}}
          </h2>
          <div>
            <p style="margin-bottom:2;font-size: 1.4rem;" :class="`font-weight-bold ${year.color}--text`">
              {{year.company}}
            </p>
            <v-icon :color="year.color">
              {{year.icon}}
            </v-icon>
            
            {{year.location}} <span style="padding-left: 30px;font-size: 0.9rem;" :class="`font-weight-bold ${year.color}--text`">{{year.duration}}</span>
          </div>
          <div :style="'font-size:0.9rem; text-align:'+ year.justify +';'">
            <p style="padding:0;margin:0" v-for = "(desc, i) in year.description" :key="i">
              {{desc}}
            </p>
          </div>
        </div>
      </v-timeline-item>
    </v-timeline>
    <v-timeline v-else align-top dense >
      <v-timeline-item v-for="(year, i) in years" :key="i" :color="year.color" >
        <span
            :class="`headline font-weight-bold ${year.color}--text`"
            v-text="year.year"
          ></span>
          <div class="py-4">
          <h2 :class="`headline font-weight-light mb-4 ${year.color}--text`" data-cursor-hover>
            {{year.title}}
          </h2>

          <div>
            <p style="margin-bottom:2;font-size: 1.4rem;" :class="`font-weight-bold ${year.color}--text`">
              {{year.company}}
            </p>
            <v-icon :color="year.color">
              {{year.icon}}
            </v-icon>
            {{year.location}}
            <p style="font-size: 0.9rem;" :class="`font-weight-bold ${year.color}--text`">{{year.duration}}</p>
          </div>
          <div :style="'font-size:0.9rem; text-align:'+ year.justify +';'">
            <p v-for = "(desc, i) in year.description" :key="i">
              {{desc}}
            </p>
          </div>
        </div>
        
      </v-timeline-item>
    </v-timeline>
  </div>
</div>
  </template>
  
  <script>
    export default {
        name: 'ExperienceVue',
        mounted() {
          if (this.$vuetify.breakpoint.name === 'sm' || this.$vuetify.breakpoint.name === 'xs') {
            this.isRenderTimeline1 = false
            document.getElementsByClassName('divWidth')[0].style.margin = '0 0px';
            document.getElementsByClassName('divWidth')[0].style.marginRight = '50px'
            document.getElementsByClassName('seconda')[0].innerHTML = 'Experience'
            document.getElementsByTagName('h1')[4].style.padding = '0'
            document.getElementsByTagName('h1')[4].style.paddingLeft = '5px'
            document.getElementsByTagName('h1')[4].style.fontSize = '3rem'
          } else {
            this.isRenderTimeline1 = true
          }
        },
      data: () => ({
        isRenderTimeline1: true,
        years: [
          {
            company: 'GreyJay Energy',
            color: 'cyan',
            duration: '06/2022 - 08/2022',
            year: '2022',
            title: 'Web Development Intern',
            location: 'Edmonton, AB',
            icon: 'mdi-map-marker-outline', 
            justify: 'start',
            
            description: [
              '● Developed an android app that visualizes energy usage and empowers users to make informed decisions, resulting in a 20% reduction in energy consumption by end-users.',
              '● Created customized widgets in the app using Vue.js and Javascript to improve the user experience and enhance the functionality of the app',
              '● Integrated push notifications in the app with Google Firebase to ensure timely updates and alerts for users',
              "● Conducted log-linear analysis on data using Python's Scikit-Learn (sklearn) library to make future predictions and used Vue.js and ChartJs to create UI chart components",
            ],
          },
          {
            company: 'Better Drones',
            color: 'green',
            duration: '10/2018 - 01/2019',
            year: '2018',
            title: 'Drone Engineering Intern',
            location: 'Noida, India',
            icon: 'mdi-map-marker-outline',
            justify: 'start',
            description: [
              '● Led team’s efforts of making quad-rotor drones by assembling, soldering various components, and programming them with ArduPilot firmware; resulted in faster production by 15%.', 
              '● Analyzed options available for client needs and recommended solutions based on time and resource considerations, which led to acquiring 3 new projects.',
              '● Developed reports and quotations about project specifications for clients based around their requirements and budget.'
            ],
            
          },
        ],
      }),
    }
  </script>
  <style>
     @import url('https://fonts.googleapis.com/css2?family=Ubuntu&display=swap');
        .prima {
        font-weight: 900;
        font-style: normal;
        color: #8CF2D8;
        margin-right: 12px;
        padding-right: 12px;
    }
    .seconda{
        font-weight: 900;
        font-style: normal;
        margin-left: 12px;
        padding-left: 12px;
        color: #009688;
    }
    .divWidth {
      margin: 0px 100px
    }
    .mainheader {
      text-align:center;font-size: 5rem;
    }
    h1{
        font-family: 'Ubuntu';
        font-style: normal;
        font-size: 5rem;
    }
    .contain {
      position: relative;
    }
    .centered {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: transparent;
  -webkit-text-stroke-width: 1px;
  -webkit-text-stroke-color: #8CF2D8;
  font-size: 200px;
  opacity: 20%;
}
  </style>