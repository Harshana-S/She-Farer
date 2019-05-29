<template>
<html>
<head>
    
</head>
<body>
<div>
<v-stepper ref="stepper" :steps="5" v-model="step"></v-stepper>

<div v-if="step === 1">
    <section id="selectDestination">
    <h3>Select Destination</h3>
    <div class="container"></div>
    <div class="searchText">
    <form id="destination">
    <input id="searchbar" placeholder="Enter your search destination" v-model="destination"/>
    {{destination}}
    </form>
    </div>
    <br/>
    <div class="buttons">
    <button id="button_enter"  v-on:click.prevent="logDestination">Enter</button>
    </div>    
    <div class="datesJourney">
        <div style="width:50vw;float:left;">
            Start Journey date
            <datepicker v-model="sdate" name="startDate" @input="logStartDate">
            </datepicker>
        </div>
        <div style="width:50vw;float:right;">
            End Journey date
            <datepicker v-model="edate" name="endDate" @input="logEndDate">
            </datepicker>
        </div>
    </div>
    <div class="switchButton">
    <button type="button" @click="$refs.stepper.next()">Continue</button>
    </div>
    </section>
</div>
<div v-if="step === 2">
    <section id="Choose Places">
        <h3>Choose Places</h3>
        <div class="icons">
        <heart-icon />
        </div>
        <h5> Double Tap To Like</h5>
        <div class="card-row">
            <div class="card" 
            @mouseover="hoverCard(0)"
            @mouseout="hoverCard(-1)" @dblclick="handler(0)">
            <img class="card-image" :class="{'selected': isSelected(0)}" src="../assets/mall.png">
                    <div v-if="show[0]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                <div class="card-footer">
                    <h4 class="card-title">Malls</h4>
                </div>  
            </div>
            <div class="card"
            @mouseover="hoverCard(1)"
            @mouseout="hoverCard(-1)" @dblclick="handler(1)">
                <img class="card-image" :class="{'selected': isSelected(1)}" src="../assets/bar.png">
                    <div v-if="show[1]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Bars</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(2)"
            @mouseout="hoverCard(-1)" @dblclick="handler(2)">
                <img class="card-image" :class="{'selected': isSelected(2)}" src="../assets/tourism.png">
                    <div v-if="show[2]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                <div class="card-footer">
                    <h4 class="card-title">Tourist Attractions</h4>
                </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(3)"
            @mouseout="hoverCard(-1)" @dblclick="handler(3)">
                <img class="card-image" :class="{'selected': isSelected(3)}" src="../assets/bookstore.png">
                    <div v-if="show[3]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Bookstores</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(4)"
            @mouseout="hoverCard(-1)" @dblclick="handler(4)">
                <img class="card-image" :class="{'selected': isSelected(4)}" src="../assets/govt_building.png">
                    <div v-if="show[4]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Government Buildings</h4>
                    </div>
            </div>
        </div>
        <div class="card-row">
            <div class="card"
            @mouseover="hoverCard(5)"
            @mouseout="hoverCard(-1)" @dblclick="handler(5)">
                <img class="card-image" :class="{'selected': isSelected(5)}" src="../assets/worship.png">
                    <div v-if="show[5]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Places of Worship</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(6)"
            @mouseout="hoverCard(-1)" @dblclick="handler(6)">
                <img class="card-image" :class="{'selected': isSelected(6)}" src="../assets/parks.png">
                    <div v-if="show[6]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Parks</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(7)"
            @mouseout="hoverCard(-1)" @dblclick="handler(7)">
                <img class="card-image" src="../assets/streetfood.png">
                    <div v-if="show[7]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Street Food</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(8)"
            @mouseout="hoverCard(-1)" @dblclick="handler(8)">
                <img class="card-image" src="../assets/wildlife.png">
                    <div v-if="show[8]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Wildlife</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(9)"
            @mouseout="hoverCard(-1)" @dblclick="handler(9)">
                <img class="card-image" src="../assets/monuments.png">
                    <div v-if="show[9]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Monuments</h4>
                    </div>
            </div>
        </div>
        <div class="card-row">
            <div class="card"
            @mouseover="hoverCard(10)"
            @mouseout="hoverCard(-1)" @dblclick="handler(10)">
                <img class="card-image" src="../assets/restaurants.png">
                    <div v-if="show[10]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Restaurants</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(11)"
            @mouseout="hoverCard(-1)" @dblclick="handler(11)">
                <img class="card-image" src="../assets/lake.png">
                    <div v-if="show[11]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Lakes</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(12)"
            @mouseout="hoverCard(-1)" @dblclick="handler(12)">
                <img class="card-image" src="../assets/itpark.png">
                    <div v-if="show[12]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">IT Parks</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(13)"
            @mouseout="hoverCard(-1)" @dblclick="handler(13)">
                <img class="card-image" src="../assets/nature.png">
                    <div v-if="show[13]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Nature</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(14)"
            @mouseout="hoverCard(-1)" @dblclick="handler(14)">
                <img class="card-image" src="../assets/bazaar.png">
                    <div v-if="show[14]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Bazaars</h4>
                    </div>
            </div>
        </div>
        <div class="card-row">
            <div class="card"
            @mouseover="hoverCard(15)"
            @mouseout="hoverCard(-1)" @dblclick="handler(15)">
                <img class="card-image" src="../assets/art_museum.png">
                    <div v-if="show[15]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Art Galleries</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(16)"
            @mouseout="hoverCard(-1)" @dblclick="handler(16)">
                <img class="card-image" src="../assets/museum.png">
                    <div v-if="show[16]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Museums</h4>
                    </div>
            </div>
            <div class="card"
            @mouseover="hoverCard(17)"
            @mouseout="hoverCard(-1)" @dblclick="handler(17)">
                <img class="card-image" src="../assets/amusement.png">
                    <div v-if="show[17]">
                        <transition name="bounce">
                            <div class="likedIcons icons">
                                <heart-icon />
                            </div>
                        </transition>
                    </div>
                    <div class="card-footer">
                        <h4 class="card-title">Amusement Parks</h4>
                    </div>
            </div>
        </div>
        <div class="switchButtons">
            <button @click="$refs.stepper.previous()">Back</button>
            <button @click="$refs.stepper.next()">Next</button>
        </div>
    </section>
</div>
<div v-if="step === 3">
    APP
    <button @click="$refs.stepper.next()">Next</button>
    <button @click="$refs.stepper.previous()">Back</button>
</div>
<div v-if="step === 4">
<div>
    <l-map :zoom="zoom" :center="center" style="height: 100vh; width: 100vw;">
    <l-tileLayer :url="url" :attribution="attribution"></l-tileLayer>
    <l-marker 
    v-for="(marker,index) in markers" :key="index"
    :lat-lng=marker></l-marker>       
      </l-map>
<div class="switchButtons">
    <button @click="$refs.stepper.previous()">Back</button>
    <button @click="$refs.stepper.next()">Next</button>
</div>
</div>
</div>
<div v-if="step === 5">
    APP
    <button @click="$refs.stepper.previous()">Back</button>
</div>
</div>
</body>
</html>
</template>

<script>

import { VStepper } from 'vue-stepper-component'
import Datepicker from 'vuejs-datepicker'
import moment from 'moment'
import { mapfields } from 'vuex-map-fields'
import HeartIcon from "vue-material-design-icons/Heart.vue"
import MapBox from 'mapbox-gl-vue'
import {LMap, LTileLayer, LMarker } from 'vue2-leaflet';

const cards= [
            'Malls','Bars','Tourism',
            'Bookstores','Government Buildings','Places of Worship',
            'Parks','Street Food','Wildlife',
            'Monuments','Restaurants','Lakes',
            'IT Parks','Nature','Bazaars',
            'Art Galleries','Museums','Amusement Parks'
]

var show=[
    false,false,false,
    false,false,false,
    false,false,false,
    false,false,false,
    false,false,false,
    false,false,false,
]

var latlong=
[{lat: 12.9763472,lng: 77.5929284},
{lat: 12.800285,lng:	77.5770474},
{lat: 12.9427052,lng: 77.5694287}]
export default {
name: "Stepper",
  components: {
    VStepper,
    Datepicker, 
    HeartIcon,
    MapBox,
    LMap,
    LTileLayer,
    LMarker 
  },
  
  data:function(){
      return{
          steps: 5,
          step: undefined,
          destination:'',
          sdate: '',
          edate:'',
          cards: cards,
          selectedCards: -1,
          places:[],
          show:show,
          map: null,
           zoom: 12,
            center: [12.9427052,77.5694287],
            url: 'http://{s}.tile.osm.org/{z}/{x}/{y}.png',
            attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
            markers: latlong,
      }
  },
  methods:{
      increaseStep:function(){
          this.step=this.step+1;
      },
      logDestination:function(){
          alert(this.destination);
          
          this.destination='';
      },
      logStartDate:function(){
          alert(moment(this.sdate).format('MMMM Do YYYY, h:mm:ss a'));
          
      },
      logStartDate:function(){
          alert(moment(this.edate).format('MMMM Do YYYY, h:mm:ss a'));
          
      },
       hoverCard(selectedIndex) {
            this.selectedCard = selectedIndex
      },
      isSelected(cardIndex) {
        return this.selectedCard === cardIndex
      },
      addPlace(cardIndex){
          //this.places.push(this.cards[cardIndex])
          console.log(this.cards[cardIndex]);
          //console.log(places);
      },
      invertShow(arg){
       this.$set(this.show, arg, true)
       console.log(this.show[arg]);
       //alert(this.show[arg])
      },
      handler:function(arg){
          this.addPlace(arg);
          this.invertShow(arg)
      }
  },

}
</script>

<style scoped>
@import "~leaflet/dist/leaflet.css";
.card-image {
  position: absolute;
  left: -9999px;
  right: -9999px;
  margin: auto;
  height: 200px;
  min-width: 200px;
}
.card-footer{
    position: absolute;
    bottom: 0;
    font-family: Helvetica;
}
.card {
  position: relative;
  background-color: rgb(255, 255, 255);
  height: 300px;
  width: 240px;
  margin-top: 0px;
  margin-left: 10px;
  margin-right: 10px;
  margin-bottom: 0px;
  overflow: hidden;
  box-shadow: 0px 2px 4px 0px rgba(0,0,0,0.5);
}
.card-row {
  display: flex;
  justify-content: center;
  align-items: center;  
  min-width: 780px;
  width: 100%;
  height: 500px;
}
.card {
  /* the other rules */
  transition: height 0.3s, box-shadow 0.3s;
}
.card:hover {
  height: 360px;
  box-shadow: 20px 20px 40px 0px rgba(0,0,0,0.5);
}
.card:active{
    height: 400px;
}
.card-image {
  /* the other rules */
  transition: height 0.3s, opacity 0.3s;
}
.card-image.selected {
  height: 410px;
  opacity: 0.3;
}
#stepper_header{
    flex-direction: row;
    align-items: stretch;
}
.searchText{
    margin-left: 20vw;
    margin-right: 20vw;
    height: 10vh;
    font-size: 4.5vh;
}
#searchbar{
    width: 100%;
}
#textbox{
    flex-flow: row;
    align-items: center;
}
.container{
    width: auto;
    height: 100px;
}
.buttons{
    flex-direction: row;
}
button{
    margin: auto;
    display: block;
}
button{
  padding:16px 32px;
  font-family:helvetica;
  font-size:16px;
  font-weight:100;
  color:#fff;
  background: #587286;
  border:0;
  font-weight:100;
}
button:hover{
  background: #3B5C76;
}
.switchButton{
    margin-right: 40px;
    width: auto;
    flex-direction: row;
    align-items: flex-end;
    float: right;
}
h3{
    text-align: center;
}
h5{
    text-align: center;
}
.datesJourney{
    width: 100vw;
    margin: 5vw;
}
.icons{
    text-align: center;
    color: red;
}
.likedIcons{
    position: absolute;
    bottom: 15%;
    float: right;
}
.bounce-transition {
  display: inline-block; /* otherwise scale animation won't work */
}
.bounce-enter {
  animation: bounce-in .5s;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
.switchButtons{
    display: flex;
    justify-content: center;
    align-items: center;  
}
#map {
  width: 100%;
  height: 500px;
}
</style>


