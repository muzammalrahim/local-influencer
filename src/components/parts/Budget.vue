<template>
    <div class="row bg_white rounded-5 m-0 mt-3">
        <div class="col-md-12">
        <h5 class="py-2 px-2">Budget</h5>
        <hr>
        <h2 class="ps-2">
            <strong>
                {{ campaign.campaignEstimate !== undefined ? campaign.campaignEstimate.buget : '' }}
            </strong> 
            <small class="fs-4">
                Total Budget
            </small>
        </h2>
        <h5 class="text-secondary ps-2">
            {{ campaign.campaignEstimate !== undefined ? campaign.campaignEstimate.reach : '' }} Estimated Reach
        </h5>
        <p class="followers px-2">
            Influencers 
            <span class="float-right rounded-pill px-2" id="demo1">+</span> 
        </p>
        <!-- Range Starts here -->
        <div class="slidecontainer px-2">
            <input type="range" min="1" max="100" value="50" class="slider" id="myRange1">
            
        </div>
        <!-- range ends here -->
        <p class="followers px-2">
            Posts 
            <span class="float-right rounded-pill px-2" id="posts">{{ campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.posts : '' }}</span> 
        </p>
        <!-- Range Starts here -->
        <div class="slidecontainer px-2">
            <input type="range" min="1" max="1000" class="slider" id="myRange2" v-bind:value="campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.posts : ''">
        </div>
        <!-- range ends here -->
        <a href="" class="Continue-btn my-3 mx-2">Continue</a>
        </div>
    </div>
</template>


<script>
export default {

  props: {
    campaign: {
      type: Object,
    },
  },

  mounted () {
    // Posts range slider
    var slider2 = document.getElementById("myRange2");
    var output2 = document.getElementById("posts");
    output2.innerHTML = slider2.value;
    
    slider2.oninput = function() {
      output2.innerHTML = this.value;
    }
  }
}
</script>