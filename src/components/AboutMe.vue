<template>
    <v-app style="display:block" >
        <vue-threejs-birds
        id="birds"
    :quantity="quantity" 
    :canvasBgColor="canvasBgColor" 
    :effectController="{
      separation: 20.0,
      alignment: 20.0,
      cohesion: 20.0,
      freedom: 1
    }"
  />
        <!-- <cursor-fx :config="BASE_CONFIG" color='#1DE9B6' color-hover='#FF8A65'/> -->
        <div class="mainContainer" style="margin:auto 0px">
                        <h1 style="margin:0px" class="primary-text">
                            <p class="upperText" >Hi, my name is </p>
                            <p style="margin:0px;line-height: normal;"><span data-cursor-hover style="margin:0px">Akarshan</span></p>
                            <p style="margin:0px; padding-left: 90px;line-height: normal;" ><span data-cursor-hover >Mishra</span></p>
                        </h1>
                        <h1>
                        <p class="bottomText">I am a
                        <vue-typer
                            data-cursor-hover
                            :text='["Creative", "Designer", "Developer"]'
                            :repeat='Infinity'
                            :shuffle='false'
                            initial-action='typing'
                            :pre-type-delay='70'
                            :type-delay='70'
                            :pre-erase-delay='2000'
                            :erase-delay='250'
                            erase-style='select-back'
                            :erase-on-complete='false'
                            caret-animation='phase'
                        />
                    </p>
                        </h1>
                        

        </div>

    </v-app>
</template>

<script>
    import { VueTyper } from 'vue-typer'
    import VueThreejsBirds from 'vue-threejs-birds'
    import { defineComponent } from 'vue';
    export default defineComponent({
        mounted() {
            // The point of this is to figure out the appropriate CSS for each display size
            // alert(this.$vuetify.breakpoint.name)
            window.addEventListener('resize', this.handleResize)
            if (this.$vuetify.breakpoint.name === 'sm' || this.$vuetify.breakpoint.name === 'xs') {
                document.getElementsByClassName('vue-typer')[0].style.fontSize = '2rem'
                document.getElementsByClassName('primary-text')[0].style.fontSize = '3.5rem'
                document.getElementsByClassName('bottomText')[0].style.fontSize = '2rem'
                document.getElementsByClassName('upperText')[0].style.fontSize = '2rem'
                // document.getElementsByClassName('mainContainer')[0].style.paddingTop = '50%'
                document.getElementsByClassName('mainContainer')[0].style.marginRight = '5%'
            } 
        },
        components: {
            'vue-typer': VueTyper,
            VueThreejsBirds,
        },
        methods: {
        handleResize() {
          const windowSize = {
            width: window.screen.availWidth,
            height: window.screen.availHeight
            
          }
          this.$root.$emit('resized', windowSize)
        }
      },
      beforeDestroy() {
        window.removeEventListener('resize', this.handleResize)
      },
        data () {
            const BASE_CONFIG = {
                lerps: {
                    dot: 1,
                    circle: 0.18,
                    custom: 0.23,
                },
                scale: {
                    ratio: 0.18,
                    min: 0.7,
                    max: 1,
                },
                opacity: 0.1,
            };
            return {
                BASE_CONFIG,
                quantity: 3,
          canvasBgColor: "#fff"
            }
        }
    })
</script>

<style >
@import url('https://fonts.googleapis.com/css2?family=Ubuntu&display=swap');
@keyframes rocking {
  0%,100% {transform: rotateZ(-10deg);}
  50%     {transform: rotateZ(10deg);}
}

.vue-typer {
    font-family: 'Ubuntu';
    font-style: normal;
  font-weight: 700;
    font-size: 4rem;
}
.vue-typer .custom.char.typed {
    color: #009688;
}
.vue-typer .custom.char.selected {
    /* COLOR FOR CHAR */
    /* color: #E91E63; */
}

.vue-typer .custom.caret {
    animation: rocking 1s ease-in-out 0s infinite;
}
.vue-typer .custom.caret.typing {
    background-color: #02cecb;
}
.vue-typer .custom.caret.selecting {
    display: inline-block;
    background-color: #fdc2b0;
}
.text-secondary {
    padding-left:75px;
    padding-top: 0px;
    padding-bottom: 5px;
}
.primary-text {
    font-family: 'Ubuntu';
    font-style: normal;
  font-weight: 900;
  color:#009688;
  line-height: normal;
    font-size: 7rem;
}
.bottomText {
    font-size:3rem;color:#8CF2D8;margin:0;padding:0
}
.upperText {
    font-size:3rem;color:#8CF2D8;margin:0;padding:0;
}
.mainContainer {
    text-align:center;z-index:1;
}

</style>