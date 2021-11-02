<template>
  <div class="container-fluid">
    <Header />

    <!-- buttons -->
    <div class="container ">
      <div class="row d-none d-md-block">
          <div class="col-10 py-3"> 
            <a class="text-dark text-decoration-none tab_btn rounded px-1 py-2 mx-1"><img src="assests/users.svg" class="img" alt=""><img src="assests/users1.svg" class="d-none hover-img" alt=""> Influencers</a>
            <a class="text-dark text-decoration-none tab_btn  rounded px-1 py-2 mx-1 Active"><img src="assests/compaign.svg" class="img" alt=""><img src="assests/compaign.svg" class="d-none hover-img" alt=""> Campaign</a>
            <a class="text-dark text-decoration-none tab_btn  rounded px-4 py-2 mx-1"><img src="assests/tags.svg" class="img" alt=""><img src="assests/tags1.svg" class="d-none hover-img p-1" alt=""> Deal</a>
          </div>
      </div>
      <div class="row">
          <div class="col-md-6 ">
            
            <Target v-bind:campaign="campaign" />
            <Budget v-bind:campaign="campaign" />
          </div>
          <div class="col-md-6 second-widjet" style="height: fit-content;">
            <Audience v-bind:campaign="campaign" />
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './commons/Header.vue'
import Target from './parts/Target.vue'
import Budget from './parts/Budget.vue'
import Audience from './parts/Audience.vue'
import axios from 'axios'

export default {
  name: 'Campaign',

  components: {
    Header,
    Target,
    Budget,
    Audience,
  },

  data() {
    return {
      campaign: {},  
    }
  },

  // using asyn await
  async mounted() {
    try {
      var result = await axios({
        method: "POST",
        url: "http://instars.hostify.one/graphql",
        data: {
          query: `
              query NewCampaign{
                campaignFilterLimits {
                  followers,
                  locations{
                    id
                    name
                  }
                }
                campaignDefaultFilter {
                  followers
                  priceStart
                  priceEnd
                  rating
                  ageStart
                  ageEnd
                  gender
                  location
                  interests
                  posts
                }
                campaignEstimate {
                  reach,
                  buget
                }
              }
          `
        }
      });

      // assigning response data to campaign
      this.campaign = result.data.data;
    } catch (error) {
      console.error(error);
    } 

    var guage_arc = document.getElementById('type-unique-id');

    guage_arc.children[0].children[6].innerHTML = 'Specific';
    guage_arc.children[0].children[6].style.fontSize = '13px';
    guage_arc.children[0].children[7].innerHTML = 'Broad';
    guage_arc.children[0].children[7].style.fontSize = '13px';

    var slider = document.getElementById("myRange");
    var output = document.getElementById("demo");
    output.innerHTML = slider.value;
    
    slider.oninput = function() {
      output.innerHTML = this.value;
    }
    // html for second single range slider
    var slider1 = document.getElementById("myRange1");
    var output1 = document.getElementById("demo1");
    output1.innerHTML = slider1.value;
    
    slider1.oninput = function() {
      output1.innerHTML = this.value;
    }
    
    
    // Multislider range
    function getVals(){
      // Get slider values
      var parent = this.parentNode;
      var slides = parent.getElementsByTagName("input");
        var slide1 = parseFloat( slides[0].value );
        var slide2 = parseFloat( slides[1].value );
      // Neither slider will clip the other, so make sure we determine which is larger
      if( slide1 > slide2 ){ var tmp = slide2; slide2 = slide1; slide1 = tmp; }
      
      var displayElement = parent.getElementsByClassName("rangeValues")[0];
      displayElement.innerHTML =slide1 + "-" + slide2;
    }

    window.onload = function(){
      // Initialize Sliders
      var sliderSections = document.getElementsByClassName("range-slider");
      for( var x = 0; x < sliderSections.length; x++ ){
        var sliders = sliderSections[x].getElementsByTagName("input");
        for( var y = 0; y < sliders.length; y++ ){
          if( sliders[y].type ==="range" ){
            sliders[y].oninput = getVals;
            // Manually trigger event first time to display values
            sliders[y].oninput();
          }
        }
      }
    }                    
  }
}
</script>

<!-- Added "scoped" attribute to limit CSS to this component only -->
<style>
 .__range{
    -webkit-appearance: none;
    background-color: #e5e7e9;
    height: 3px;
    width: 95%;
  }
  .__range:focus{
    outline:none;
  }
  .__range::-webkit-slider-thumb{
    -webkit-appearance: none;
    width: 20px;
    height: 20px;
    background: #ffffff;
    border-radius: 50%;
    border: 2px solid #9637f3;
    cursor: -moz-grab;
    cursor: -webkit-grab;
    z-index:999; 
  }

  section.range-slider {
    position: relative;
    width: 100%;
    height: 75px;
  }

  section.range-slider input {
    pointer-events: none;
    position: absolute;
    left: 16px;
    top: 45px;
    width: 95%;
    outline: none;
    height: 5px;
    margin: 23px  0;
    padding: 0;
  }

  section.range-slider input::-webkit-slider-thumb {
    pointer-events: all;
    position: relative;
    z-index: 1;
    outline: 0;
  }
</style>
