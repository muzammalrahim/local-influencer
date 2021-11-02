<template>
  <div class="row bg_white rounded-5 m-0 ">
    <h5 class="p-3">Target</h5>
    <hr>
    <div class="col-12 ">
      <h3 class="py-5 px-2"><strong>45</strong> <small class="fs-4">Local Influencers availible</small></h3>
      <p class="followers px-2">followers 
        <span class="float-right rounded-pill px-2" id="demo"> 
          {{ campaign.campaignFilterLimits !== undefined ?  campaign.campaignFilterLimits.followers : '' }}
        </span></p>
      <!-- Range Starts here -->
      <div class="slidecontainer px-2">
          <input type="range" min="1" max="1000" :value="campaign.campaignFilterLimits !== undefined ?  campaign.campaignFilterLimits.followers : ''" class="slider" id="myRange">
          <!-- <p>Value: <span id="demo"></span></p> -->
      </div>
      <!-- range ends here -->
      <section class="range-slider">
        <p class="followers py-3 px-2">Price Rage /Post <span class="float-right rounded-pill px-2 rangeValues">{{ campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.priceStart : '' }} - {{ campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.priceEnd : '' }}</span> </p>
        <span class=""></span>
        <input v-bind:value="campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.priceStart : ''" min="0" max="50" step="1" type="range" class="__range">
        <input v-bind:value="campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.priceEnd : ''" min="0" max="50" step="1" type="range" class="__range" >
      </section>   
      <p class="px-2">Rating</p>
      <p class="rating-star px-2"><i class="fas fa-star px-1"></i> <i class="fas fa-star px-1"></i> <i class="fas fa-star px-1"></i> <i class="fas fa-star px-1"></i> <i class="fas fa-star px-1"></i></p>
      <button class="accordion">
          <p class="mb-1 text-secondary fw-bold">Age and Gender</p>
          <span>{{ campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.ageStart : '' }}-{{ campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.ageEnd + '+' : '' }}| 
            {{ campaign.campaignDefaultFilter !== undefined && campaign.campaignDefaultFilter.gender == 0 ? 'All' : '' }}
            {{ campaign.campaignDefaultFilter !== undefined && campaign.campaignDefaultFilter.gender == 1 ? 'Male' : '' }}
            {{ campaign.campaignDefaultFilter !== undefined && campaign.campaignDefaultFilter.gender == 2 ? 'Female' : '' }}
          </span>
      </button>
      <div class="panel">
          <div class="tab" role="tabpanel">
            <!-- Nav tabs -->
            <ul class="nav nav-tabs" role="tablist">
                <li role="presentation" class="px-2" v-bind:class="campaign.campaignDefaultFilter !== undefined && campaign.campaignDefaultFilter.gender == 0 ? 'active' : ''"><a href="#Section1" aria-controls="home" role="tab" data-toggle="tab" class="px-3">All</a></li>
                <li role="presentation" class="px-2" v-bind:class="campaign.campaignDefaultFilter !== undefined && campaign.campaignDefaultFilter.gender == 2 ? 'active' : ''"><a href="#Section2" aria-controls="profile" role="tab" data-toggle="tab" class="px-3">Women</a></li>
                <li role="presentation" v-bind:class="campaign.campaignDefaultFilter !== undefined && campaign.campaignDefaultFilter.gender == 2 ? 'active' : ''"><a href="#Section3" aria-controls="messages" role="tab" data-toggle="tab" class="px-3">Male</a></li>
            </ul>
            <!-- Tab panes -->
            <div class="tab-content tabs">
                <div role="tabpanel" class="tab-pane fade  " id="Section1">
                  section1
                  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce semper, magna a ultricies volutpat, mi eros viverra massa, vitae consequat nisi justo in tortor. Proin accumsan felis ac felis dapibus, non iaculis mi varius.</p>
                </div>
                <div role="tabpanel" class="tab-pane fade in active" id="Section2">
                  <div class="range-portion py-2">
                    <section class="range-slider">
                    <p class="followers py-3 px-4">Age 
                      <span class="float-right rounded-pill px-2 rangeValues"> {{ campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.ageStart : '' }}{{ campaign.campaignDefaultFilter !== undefined ?  '-' + campaign.campaignDefaultFilter.ageEnd : '' }} </span> </p>
                    <span class=""></span>
                    <input v-bind:value="campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.ageStart : ''" min="16" max="65" step="1" type="range" class="__range">
                    <input v-bind:value="campaign.campaignDefaultFilter !== undefined ?  campaign.campaignDefaultFilter.ageEnd : ''" min="16" max="65" step="1" type="range" class="__range" >
                  </section>
                    </div> 
                </div>
                <div role="tabpanel" class="tab-pane fade" id="Section3">
                  section3
                  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce semper, magna a ultricies volutpat, mi eros viverra massa, vitae consequat nisi justo in tortor. Proin accumsan felis ac felis dapibus, non iaculis mi varius.</p>
                </div>
            </div>
          </div>
      </div>
      <button class="accordion">
          <p class="mb-1 text-secondary fw-bold">Location</p>
          <span>
            {{ campaign.campaignDefaultFilter !== undefined && campaign.campaignDefaultFilter.location == 0 ? 'Entire Country' : 'Other Location' }}
          </span>
      </button>
      <div class="panel">
          <form action="">
            <Select name="" class="form-control mb-2">
                <option value="0">All</option>
                <option value="1">Iasi</option>
                <option value="2">Botosani</option>
                <option value="3">Boston</option>
                <option value="4">London</option>
                <option value="5">Paris</option>
                <option value="6">Milan</option>
                <option value="7">Las Vegas</option>
                <option value="8">Rome</option>
                <option value="9">Athena</option>
            </Select>
          </form>
      </div>
      <button class="accordion">
          <p class="mb-1 text-secondary fw-bold">Intrests</p>
          <span>{{ campaign.campaignDefaultFilter !== undefined && campaign.campaignDefaultFilter.location == 0 ? 'All' : 'My Interest' }}</span>
      </button>
      <div class="panel">
          <ul class="border rounded p-0 my-2">
            <li class="border-bottom bg-light py-2 px-1">Beauty</li>
            <li class="border-bottom bg-light py-2 px-1">All </li>
            <li class="border-bottom bg-light py-2 px-1">Blogger</li>
            <li class="border-bottom bg-light py-2 px-1"> Sports </li>
            <li class="border-bottom bg-light py-2 px-1"> Games</li>
          </ul>
      </div>
      <button class="accordion">
          <p class="mb-1 text-secondary fw-bold">Quality files</p>
          <span>All</span>
      </button>
      <div class="panel">
          <div class="row">
            <div class="col-md-12">
                <h5><Strong><big>45</big></Strong> Influencers availible</h5>
            </div>
            <div class="col-md-6">
                <span class="q-heading">Minimum Rating of influencers</span>
                <p class="rating-star"><i class="fas fa-star px-1"></i> <i class="fas fa-star px-1"></i> <i class="fas fa-star px-1"></i> <i class="fas fa-star px-1"></i> <i class="fas fa-star px-1"></i></p>
            </div>
            <div class="col-md-6">
                <span class="q-heading">colaborations made by influencers</span>
                <p class="followers2"><span class=" rounded-pill px-2">1+</span> <span class=" rounded-pill px-2">5+</span> <span class=" rounded-pill px-2">10+</span></p>
            </div>
          </div>
      </div>
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
    var acc = document.getElementsByClassName("accordion");
    var i;
  
    for (i = 0; i < acc.length; i++) {
      
      acc[i].addEventListener("click", function() {
        this.classList.addClass("Active1");
        var panel = this.nextElementSibling;
        if (panel.style.maxHeight) {
          panel.style.maxHeight = null;
        } else {
          panel.style.maxHeight = panel.scrollHeight + "px";
        } 
      });
    }
  }
  
}
</script>