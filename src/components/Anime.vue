<template>
  <div class="Anime" ref="Anime" @click="callMode">
    <!-- <svg width="1000" height="1000" xmlns="http://www.w3.org/2000/svg" id="abc">
      <path d="M 150 250
A 100 100 0 1 0 350 250
A 100 100 0 1 0 150 250
" stroke="black" fill="transparent" id="warai"/>
    </svg> -->
  </div>
</template>

<script>

import anime from 'animejs';
export default {
  data() {
    return {
      frameX:0,
      frameY:0,
      mode:2,
      //ougi
      ougiR:420,
      //garcon
      order:[],
      phase:0,
    }
  },
  mounted(){
    //svgエレメントの作成
    let svg = document.createElementNS("http://www.w3.org/2000/svg", "svg:svg")
    this.frameX=this.$refs.Anime.clientWidth
    this.frameY=this.$refs.Anime.clientHeight
    svg.setAttribute('width',this.frameX)
    svg.setAttribute('height',this.frameY)
    svg.setAttribute('id','svg')
    this.$refs.Anime.appendChild(svg)
    var lineDrawing = anime({
      targets: '#warai',
      strokeDashoffset: [anime.setDashoffset, 0],
      easing: 'easeInOutExpo',
      duration: 1000,
      delay: function(el, i) { return i * 150 },
    });

    this.garcon()
    // let timerID = setInterval(this.modeMGMT, 7000);
  },
  methods:{
    callMode(){
      switch (this.mode) {
        case 0:
          this.bezierClick()
          break;
        case 1:
          this.ougiClick()
          break;
        case 2:
          this.garconClick()
          break;
      }
    },
    bezier(){
      console.log("おちゃんせすっす")
      this.createBZPath(0,0,Math.floor(this.frameX/2)-400,0,Math.floor(this.frameX/2)-400,this.frameY,0,this.frameY)
      this.createBZPath(this.frameX,0,Math.floor(this.frameX/2)+400,0,Math.floor(this.frameX/2)+400,this.frameY,this.frameX,this.frameY)
      this.createBZPath(0,0,0,Math.floor(this.frameY/2)-150,this.frameX,Math.floor(this.frameY/2)-150,this.frameX,0)
      this.createBZPath(0,this.frameY,0,Math.floor(this.frameY/2)+150,this.frameX,Math.floor(this.frameY/2)+150,this.frameX,this.frameY)
      // this.createBZPath(0,0,0,Math.floor(this.frameY/2),Math.floor(this.frameX/2),this.frameY,this.frameX,this.frameY)
      // this.createBZPath(this.frameX,0,this.frameX,Math.floor(this.frameY/2),Math.floor(this.frameX/2),this.frameY,0,this.frameY)
      // this.createBZPath(0,this.frameY,0,Math.floor(this.frameY/2),Math.floor(this.frameX/2),0,this.frameX,0)
      // this.createBZPath(this.frameX,this.frameY,this.frameX,Math.floor(this.frameY/2),Math.floor(this.frameX/2),0,0,0)
      var lineDrawing = anime({
        targets: '#svg path',
        strokeDashoffset: [anime.setDashoffset, 0],
        easing: 'easeInOutExpo',
        duration: 1000,
        delay: function(el, i) { return i * 150 },
      });
    },
    bezierClick(){
      let seed=Math.floor(Math.random() * 201) - 100
      let seed1=Math.floor(Math.random() * 201) - 100
      let seed2=Math.floor(Math.random() * 201) - 100
      let seed3=Math.floor(Math.random() * 201) - 100

      switch (Math.floor(Math.random() * 8)) {
        case 0:
          this.createBZPath(0,0,Math.floor(this.frameX/2)-400+seed,0+seed1,Math.floor(this.frameX/2)-400+seed2,this.frameY+seed3,0,this.frameY)
          break;
        case 1:
          this.createBZPath(this.frameX,0,Math.floor(this.frameX/2)+400+seed,0+seed1,Math.floor(this.frameX/2)+400+seed2,this.frameY+seed3,this.frameX,this.frameY)
          break;
        case 2:
          this.createBZPath(0,0,0+seed,Math.floor(this.frameY/2)-150+seed1,this.frameX+seed2,Math.floor(this.frameY/2)-150+seed3,this.frameX,0)
          break;
        case 3:
          this.createBZPath(0,this.frameY,0+seed,Math.floor(this.frameY/2)+150+seed1,this.frameX+seed2,Math.floor(this.frameY/2)+150+seed3,this.frameX,this.frameY)
          break;
        case 4:
          this.createBZPath(0,0,0+seed,Math.floor(this.frameY/2)+seed1,Math.floor(this.frameX/2)+seed2,this.frameY+seed3,this.frameX,this.frameY)
          break;
        case 5:
          this.createBZPath(this.frameX,0,this.frameX+seed,Math.floor(this.frameY/2)+seed1,Math.floor(this.frameX/2)+seed2,this.frameY+seed3,0,this.frameY)
          break;
        case 6:
          this.createBZPath(0,this.frameY,0+seed,Math.floor(this.frameY/2)+seed1,Math.floor(this.frameX/2)+seed2,0+seed3,this.frameX,0)
          break;
        case 7:
          this.createBZPath(this.frameX,this.frameY,this.frameX+seed,Math.floor(this.frameY/2)+seed1,Math.floor(this.frameX/2)+seed2,0+seed3,0,0)
          break;
        default:
          break;
      }
    },
    //bezierのpath作る
    createBZPath(a,b,c,d,e,f,g,h){
      let path = document.createElementNS('http://www.w3.org/2000/svg','path');
      path.setAttribute('stroke','black')
      path.setAttribute('fill','transparent')
      let root="M "+a+" "+b+" C "+c+" "+d+", "+e+" "+f+", "+g+" "+h
      path.setAttribute('d',root)
      document.getElementById('svg').appendChild(path)
    },
    ougi(){
      console.log("おちゃんせすっす")
      //this.createCirclePath(420,90,1)
      this.createOugiPath(this.ougiR,Math.PI*3/4,-Math.PI*2/3)
      let lineDrawing = anime({
        targets: '#svg path',
        strokeDashoffset: [anime.setDashoffset, 0],
        easing: 'easeInOutExpo',
        duration: 1000,
        delay: function(el, i) { return i * 150 },
      });
    },
    ougiClick(){
      if(this.frameX<this.ougiR*2){
        this.ougiR=415
      }
      this.ougiR=this.ougiR+10
      let angle=Math.PI*3/4+Math.random()*1.04666-0.52333
      let angle1=-Math.PI*2/3+Math.random()*1.04666-0.52333
      Math.max(Math.PI*2/3,angle)
      Math.max(Math.PI/3,angle1)
      this.createOugiPath(this.ougiR,angle,angle1)
      let id='#'+'P'+this.ougiR
      console.log(angle)
      var lineng = anime({
        targets: id,
        strokeDashoffset: [anime.setDashoffset, 0],
        easing: 'easeInOutExpo',
        duration: 1000,
        delay: function(el, i) { return i * 150 },
      });
    },
    createCirclePath(r,a,d,posiX,posiY,id){//radius angle direction
      let c=Math.cos(a)
      let s=Math.sin(a)
      let x= posiX+r*c
      let y= posiY-r*s
      let x1= posiX-r*c
      let y1= posiY+r*s
      let path = document.createElementNS('http://www.w3.org/2000/svg','path');
      path.setAttribute('stroke','black')
      path.setAttribute('fill','transparent')
      path.setAttribute('stroke-width','1px')
      console.log(id)
      path.setAttribute('id',id)
      let root="M "+x+" "+y+" A "+r+" "+r+" "+0+" "+1+" "+d+" "+x1+" "+y1+" A "+r+" "+r+" "+0+" "+0+" "+d+" "+x+" "+y
      path.setAttribute('d',root)
      document.getElementById('svg').appendChild(path)
    },
    createOugiPath(r,a,a1){//radius angle direction
      let x= this.frameX/2+r*Math.cos(a)
      let y= this.frameY/2-r*Math.sin(a)
      let x1= this.frameX/2+r*Math.cos(a1)
      let y1= this.frameY/2-r*Math.sin(a1)
      let path = document.createElementNS('http://www.w3.org/2000/svg','path');
      path.setAttribute('stroke','black')
      path.setAttribute('fill','transparent')
      path.setAttribute('stroke-width','1px')
      let id='P'+r
      console.log(id)
      path.setAttribute('id',id)
      let root="M "+x+" "+y+" A "+r+" "+r+" "+0+" "+1+" "+1+" "+x1+" "+y1
      path.setAttribute('d',root)
      document.getElementById('svg').appendChild(path)
    },
    garcon(){
      //this.createCirclePath(100,1,1,this.frameX/2-500,this.frameY/2-250)
      for(let i=0;this.frameX/2>300*i+750;i++){
        this.order.push([-750-300*i,0])
        this.order.push([750+300*i,0])
      }
      for(let i=1;this.frameY>300*i;i++){
        if(i%2==1){
          this.order.push([0,-300*i])
          this.order.push([0,300*i])
          for (let j=1;this.frameX/2>300*j;j++){
            this.order.push([-j*300,-300*i])
            this.order.push([j*300,-300*i])
            this.order.push([-j*300,300*i])
            this.order.push([j*300,300*i])
          }
        }else if(i%2==0){
          for (let j=0;this.frameX/2>300*j+150;j++){
            this.order.push([-j*300-150,-300*i])
            this.order.push([j*300+150,-300*i])
            this.order.push([-j*300-150,300*i])
            this.order.push([j*300+150,300*i])
          }
        }
      }
      this.shuffle(this.order)
      // for (let j=0;j<100;j++){
      //   this.createCirclePath(80,1,1,this.frameX/2-this.order[j][0],this.frameY/2-this.order[j][1])
      // }
    },
    garconClick(){
      let id="G"+this.phase
      this.createCirclePath(80,1,1,this.frameX/2-this.order[this.phase][0],this.frameY/2-this.order[this.phase][1],id)
      var garcon = anime({
        targets: "#"+id,
        strokeDashoffset: [anime.setDashoffset, 0],
        easing: 'easeInOutExpo',
        duration: 1000,
      });
      this.phase++
    },
    shuffle(array) {
      for (let i = array.length - 1; i >= 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
      return array;
    }
  },
  update(){

  },
  computed:{
  }
}
</script>]



<style >
.Anime{
  width:100%;
  height: 100%;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: ta;
}
.svg{
  width:500px;
  height: 500px;
}
</style>
