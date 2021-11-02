<template>
    <div class="row bg_white rounded-5 m-0 ">
        <div class="col-md-6 pt-5">
            <h5>Audience Defination</h5>
            <ul class="p-0">
                <li>Location: 
                  {{ campaign.campaignDefaultFilter !== undefined && campaign.campaignDefaultFilter.location == 0 ? 'Entire Country' : 'Other Location' }}
                </li>
                <li>
                  Age : {{ campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.ageStart : '' }}{{ campaign.campaignDefaultFilter !== undefined ?  '-' + campaign.campaignDefaultFilter.ageEnd + '+' : '' }}
                </li>
                <li>Potential Reach:</li>
            </ul>
            <h5>
              <strong>
                {{ campaign.campaignEstimate !== undefined ?  campaign.campaignEstimate.reach +'.000'   : '' }} people
              </strong>
            </h5>
        </div>
        <div class="col-md-6 pt-5">
            <!-- Include chart here -->
            <vue-gauge :refid="'type-unique-id'" :options="{'needleValue':79.9,'arcDelimiters':[79.9], 'arcColors': ['#68c868']}"></vue-gauge>
        </div>
        <div class="row">
            <div class="col-md-4">
                <div class="row d-flex align-items-center second-widjet-icons">
                <div class="col-3 icon-div"><img src="assests/heart.svg" alt=""></div>
                <div class="col-9 content-div">
                    <span class="q-heading">number of influencers</span>
                    <h5><big>45</big></h5>
                </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="row d-flex align-items-center second-widjet-icons">
                <div class="col-3 icon-div"><img src="assests/arrow.svg" alt=""></div>
                <div class="col-9 content-div">
                    <span class="q-heading">Potential Reach</span>
                    <h5>
                      <big>{{ campaign.campaignEstimate !== undefined ?  campaign.campaignEstimate.reach   : '' }}</big>
                    </h5>
                </div>
                </div>
            </div>
            <div class="col-md-4">
                <div class="row d-flex align-items-center second-widjet-icons">
                <div class="col-3 icon-div"><img src="assests/handshake.svg" alt=""></div>
                <div class="col-9 content-div">
                    <span class="q-heading">Potential engagements</span>
                    <h5><big>45</big></h5>
                </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import VueGauge from 'vue-gauge'

export default {
  props: {
    campaign: {
      type: Object,
    },
  },

  name: 'Audience',

  components: {
    VueGauge,
  },

  template: `<vue-speedometer />`,

  data() {
    return {

      // init value
      value: {
        type: Number,
        required: true,
      },

      // min/max values
      minValue: {
        type: Number,
        required: true,
      },

      maxValue: {
        type: Number,
        required: true,
      },

      // tracks if the component should update as the whole or just animate the value
      // default will just animate the value after initialization/mounting
      forceRender: {
        type: Boolean,
        required: true,
      },

      width: {
        type: Number,
        required: true,
      },

      height: {
        type: Number,
        required: true,
      },

      fluidWidth: {
        type: Boolean,
        required: true,
      },

      // segments to show in the speedometer
      segments: {
        type: Number,
        required: true,
      },

      // maximum number of labels to be shown
      maxSegmentLabels: {
        type: Number,
      },

      // custom segment points to create unequal segments
      customSegmentStops: {
        type: Array,
      },

      // color strings
      needleColor: {
        type: String,
        required: true,
      },

      startColor: {
        type: String,
        required: true,
      },

      endColor: {
        type: String,
        required: true,
      },

      // custom segment colors
      segmentColors: {
        type: Array,
        required: true,
      },

      // needle transition type and duration
      needleTransition: {
        type: String,
        required: true,
      },

      needleTransitionDuration: {
        type: Number,
        required: true,
      },

      needleHeightRatio: {
        type: Number,
        required: true,
      },

      ringWidth: {
        type: Number,
        required: true,
      },

      textColor: {
        type: String,
        required: true,
      },

      // d3 format identifier is generally a string; default "" (empty string)
      valueFormat: {
        type: String,
        required: true,
      },

      // value text format
      currentValueText: {
        type: String,
        required: true,
      },

      // placeholder style for current value
      currentValuePlaceholderStyle: {
        type: String,
        required: true,
      },

      valueTextFontWeight: {
        type: String,
        required: true,
      },
    }
  },

  // using asyn await
  mounted() {
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
    // html for third single range slider
    
    
    var acc = document.getElementsByClassName("accordion");
    var i;
    
    for (i = 0; i < acc.length; i++) {
      acc[i].addEventListener("click", function() {
        this.classList.toggle("Active1");
        var panel = this.nextElementSibling;
        if (panel.style.maxHeight) {
          panel.style.maxHeight = null;
        } else {
          panel.style.maxHeight = panel.scrollHeight + "px";
        } 
      });
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