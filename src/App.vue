<template>
  <a href="https://github.com/abdochaoubii" class="github-corner" aria-label="View source on GitHub"><svg width="80" height="80" viewBox="0 0 250 250" style="fill:#151513; color:#fff; position: absolute; top: 0; border: 0; right: 0;" aria-hidden="true"><path d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z"></path><path d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2" fill="currentColor" style="transform-origin: 130px 106px;" class="octo-arm"></path><path d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z" fill="currentColor" class="octo-body"></path></svg></a>
  <a href="https://github.com/abdochaoubii" id="github-link">View source on GitHub</a>

  <div id="formi">
  <label for="input" style="color: #fff;font-weight: bold;font-size: 18px;">Enter Values:</label>
  <!-- <input type="text" id="input" name="input" v-model="inputValue"> -->
  <textarea class="for_nmb" rows="1" cols="1" wrap="hard" v-model="inputValue">
</textarea>
  <br>
  <button  @click="mychang()">Submit</button>

</div>
<!-- </form> -->
  <div id="app" style="  margin: auto;justify-content:center;display: flex;">
    
    <div class="lolty">
    <button
      class="swipe push-rr"
      style="width: 100%"
      @click="
        pushr(stb, '');
        pushr(sta, 'rr');
      "
    >
      ↑↑ rr
    </button>
    <div style="display: flex">
      <button class="swipe push-ra" @click="pushs(sta, 'sa')">⇅ sa</button>
      <div
        class="stack-a"
        @drop="onDrop($event, 'a')"
        @dragover.prevent
        @dragenter.prevent
      >
        <button class="swipe push-rra" @click="pushrr(sta, 'rra')">
          ↓ rra
        </button>

        <div
          v-for="(n, i) in sta"
          :key="i"
          class="n-item"
          :draggable="i == sta.length - 1 ? true : false"
          @dragstart="startDrag($event, 'a')"
        >
          {{ n }}
        </div>
        <div class="n-item" v-for="i in stb.length" :key="sta.length + i" />

        <button class="swipe push-ra" @click="pushr(sta, 'ra')">↑ ra</button>
      </div>
      <button class="swipe push-sa" @click="push(stb, sta, 'pa')">← pa</button>
      <div class="winner">
        <div class="sorted s_h" style="margin-top: 30px;padding: 8px;color: rgb(255 255 255);background: rgb(6, 101, 6);font-weight:bold;border-radius: 8px;">sorted</div>
        <div class="not_sorted" style="color:#f00;margin-top: 30px;padding: 2px;font-weight:bold;">Not  sorted</div>
      <button
        class="swipe push-sa"
        style="width: 70px"
        @click="
          pushs(stb, '');
          pushs(sta, 'ss');
        "
      >
        ⇅ ss ⇅
      </button>
    </div>
      <button class="swipe push-sb" @click="push(sta, stb, 'pb')">pb →</button>

      <div
        class="stack-b"
        @drop="onDrop($event, 'b')"
        @dragover.prevent
        @dragenter.prevent
      >
        <button class="swipe push-rrb" @click="pushrr(stb, 'rrb')">
          ↓ rrb
        </button>

        <div
          v-for="(n, i) in stb"
          :key="i"
          class="n-item"
          :draggable="i == stb.length - 1 ? true : false"
          @dragstart="startDrag($event, 'b')"
        >
          {{ n }}
        </div>
        <div class="n-item" v-for="i in sta.length" :key="stb.length + i" />

        <button class="swipe push-rb" @click="pushr(stb, 'rb')">↑ rb</button>
      </div>
      <button class="swipe push-ra" @click="pushs(stb, 'sb')">⇅ sb</button>
    </div>
    <button
      class="swipe push-rrb"
      style="width: 100%"
      @click="
        pushrr(stb, '');
        pushrr(sta, 'rrr');
      "
    >
      ↓↓ rrr
    </button>
    <div>
      <div>
        <button class="btn" @click="copyToCb()">COPY</button>
        <button class="btn" @click="clear()">CLEAR</button>
      </div>
      <div class="bottom_instra">
      <div style="color: #fff;">Number of instras : {{ instras.length }}</div>
      <div
        v-for="(item, i) in instras"
        :key="i"
        class="instra"
        :draggable="i == stb.length - 1 ? true : false"
        @dragstart="startDrag($event, 'b')"
      >
        {{ item }}
      </div>
      </div>
    </div>
  </div>
  <div id="instrac">
    <div id="formi1">
      <label for="input" style="color: #fff ;font-weight: bold;font-size: 18px;">Enter Instructions:</label>
      <textarea class="for_ens" rows="4" cols="50" wrap="hard" v-model="message">

  </textarea>
      <!-- <input type="text" id="input" name="input" v-model="inputValue"> -->
      <br>
      <button  @click="print_inst()">Submit</button>
    </div>
    <div class="formi2 steps">

      <div
      v-for="(item, i) in given_ins"
      :key="i"
      class="instra"
      :draggable="i == stb.length - 1 ? true : false"
      @dragstart="startDrag($event, 'b')"
      >
      {{ item }}
    </div>
  </div>
  <div class="formi3 formi2">
    <div class="container">
  <button class="prev-button" @click="prev_move()">Previous</button>
  <button class="next-button" @click="next_move()">Next</button>
  <button class="next-button" @click="clear_move()">Clear</button>
</div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function () {
    // console.log(this);
    return {
      def:  [3,5,1,4,2,6],
      sta: [],
      stb: [],
      instras: [],
      step: -1,
      given_ins: ["pb","pb","pb","rrb","pb","ra","rrb","pb","rrb","pb","rrb","rrb","rrb","rrb","pa","pa","pa","pa","pa","pa"],
      valuees: "lol",
      origin_instra: ["sa","sb","ss","pa","pb","ra","rb","rr","rra","rrb","rrr"],
      parent : document.querySelector('.steps'),
    };
  },
  beforeMount: function () {
    this.sta = [...this.def];
    console.log(this.sta);
    // this.check_sta();
  },
  methods: {
    startDrag: function (evt, stack) {
      evt.dataTransfer.dropEffect = "move";
      evt.dataTransfer.effectAllowed = "move";
      evt.dataTransfer.setData("stack", stack);
    },
    onDrop: function (evt, to_stack) {
      const from_stack = evt.dataTransfer.getData("stack");
      if (from_stack === to_stack) return;

      if (from_stack === "a") this.pushb();
      else this.pusha();
      this.check_sta();
    
    },
    push: function (st1, st2, cmd) {
      if (st1.length === 0) return;
      let a = st1.pop();
      st2.push(a);
      this.instras.push(cmd);
    },
    pushr: function (stack, cmd) {
      if (stack.length === 0) return;
      let a = stack.pop();
      stack.unshift(a);
      if (cmd !== "") this.instras.push(cmd);
    },
    pushrr: function (stack, cmd) {
      if (stack.length === 0) return;
      let a = stack.shift();
      stack.push(a);
      if (cmd !== "") this.instras.push(cmd);
    },
    check_sta: function () {
      let add = document.querySelector('.not_sorted'); 
      let rmv = document.querySelector('.sorted'); 
      if (this.sta.length === this.def.length && this.ifsorted(this.sta.reverse()))
      {
        add.classList.add('s_h');
        rmv.classList.remove('s_h');
      }
      else{
        rmv.classList.add('s_h');
        add.classList.remove('s_h');
      }

    },
    mychang: function (stack) {
      // console.log(this.inputValue.split(" ").map(Number));
      console.log(this.def);
      // this.def=this.inputValue.split(" ").map(Number);
      this.def= this.inputValue.split(" ")
                                      .map(word => word.trim())
                                      .filter(word => word !== "")
                                      .map(Number);
      console.log(this.def);
      this.clear();
      this.step=-1;
      
    },
    print_inst: function (stack, cmd) {
      this.given_ins = this.message.split("\n").filter(value => this.origin_instra.includes(value));
      this.clear();
      // console.log(this.given_ins)
    },
    clear_move: function (stack, cmd) {
      this.clear();
      // this.step=-1;
      // const elements = document.querySelectorAll('.collored');
      // elements.forEach((element) => {
      //   element.classList.remove('collored');
      // });
    },
    next_move: function () {
      if(this.step==this.given_ins.length-1)
        return;
      this.step++;
      if(this.given_ins[this.step]==='sa')
        this.pushs(this.sta, 'sa')
      if(this.given_ins[this.step]==='sb')
      this.pushs(this.sta, 'sb')
      if(this.given_ins[this.step]==='ss')
      {
        this.pushs(this.stb, '');
        this.pushs(this.sta, 'ss');
      }
      if(this.given_ins[this.step]==='rra')
        this.pushrr(this.sta, 'rra')
      if(this.given_ins[this.step]==='rrb')
        this.pushrr(this.stb, 'rrb')
      if(this.given_ins[this.step]==='rrr')
      {
        this.pushrr(this.stb, 'rrb')
        this.pushrr(this.sta, 'rra')
      }
      if(this.given_ins[this.step]==='ra')
        this.pushr(this.sta, 'ra')
      if(this.given_ins[this.step]==='rb')
        this.pushr(this.stb, 'rb')
      if(this.given_ins[this.step]==='rr')
      {
        this.pushr(this.stb, '');
        this.pushr(this.sta, 'rr');
      }
      if(this.given_ins[this.step]==='pa')
        this.push(this.stb, this.sta, 'pa')
      if(this.given_ins[this.step]==='pb')
        this.push(this.sta, this.stb, 'pb')
      let child = document.querySelector('.steps').children[this.step]; 
      child.classList.add('collored');
      this.check_sta();
      
      
    },
    prev_move: function () {
      if(this.step==-1)
      return;
      let child = document.querySelector('.steps').children[this.step]; 
      child.classList.remove('collored');
      if(this.given_ins[this.step]==='sa')
      this.pushs(this.sta, 'sa')
      if(this.given_ins[this.step]==='sb')
      this.pushs(this.sta, 'sb')
      if(this.given_ins[this.step]==='ss')
      {
        this.pushs(this.stb, '');
        this.pushs(this.sta, 'ss');
      }
      if(this.given_ins[this.step]==='rra')
      this.pushrr(this.sta, 'ra')
      if(this.given_ins[this.step]==='rrb')
      this.pushrr(this.stb, 'rb')
      if(this.given_ins[this.step]==='rrr')
      {
        this.pushrr(this.stb, 'rb')
        this.pushrr(this.sta, 'ra')
      }
      if(this.given_ins[this.step]==='ra')
      this.pushr(this.sta, 'rra')
      if(this.given_ins[this.step]==='rb')
      this.pushr(this.stb, 'rrb')
      if(this.given_ins[this.step]==='rr')
      {
        this.pushr(this.stb, '');
        this.pushr(this.sta, 'rrr');
      }
      if(this.given_ins[this.step]==='pa')
      this.push(this.sta, this.stb, 'pb')
      if(this.given_ins[this.step]==='pb')
      this.push(this.stb, this.sta, 'pa')
      this.step--;
      this.check_sta();
      // let child = document.querySelector('.steps').children[this.step]; 
      
        
      console.log(this.given_ins[this.step]);
      },
    pushs: function (stack, cmd) {
      if (stack.length < 2) return;
      let a = stack.pop();
      let b = stack.pop();
      stack.push(a);
      stack.push(b);
      if (cmd !== "") this.instras.push(cmd);
    },
    clear: function () {
      this.instras.splice(0, this.instras.length);
      this.stb.splice(0, this.stb.length);
      this.sta = [...this.def].reverse();
      this.step=-1;
      const elements = document.querySelectorAll('.collored');
      elements.forEach((element) => {
        element.classList.remove('collored');
      });
    },
    ifsorted: function (arr) {
      let second_index;
      for(let first_index = 0; first_index < arr.length; first_index++){
          second_index = first_index + 1;
          if(arr[second_index] - arr[first_index] < 0) return false;
        }
    return true;
      
    },
    copyToCb: function () {
      let res = this.instras.join("\n");
      navigator.clipboard.writeText(res).then(
        function () {
          console.log("Async: Copying to clipboard was successful!");
        },
        function (err) {
          console.error("Async: Could not copy text: ", err);
        }
      );
    },
  },
  mounted() {
    this.check_sta();
  },
};
</script>

<style>
.github-corner:hover .octo-arm{animation:octocat-wave 560ms ease-in-out}@keyframes octocat-wave{0%,100%{transform:rotate(0)}20%,60%{transform:rotate(-25deg)}40%,80%{transform:rotate(10deg)}}@media (max-width:500px){.github-corner:hover .octo-arm{animation:none}.github-corner .octo-arm{animation:octocat-wave 560ms ease-in-out}}

button{
  cursor: pointer;
}
body
{
  background: #332f23;
  background: radial-gradient(circle, #45697c 0%, #909090 100%);
  /* background: radial-gradient(circle, #d5caca 0%, #605ed9 100%); */
  }
#github-link {
  position: fixed;
  bottom: 10px;
  right: 10px;
  display: block;
  padding: 10px;
  background-color: rgba(255, 255, 255, 0.112);
  color: #333;
  text-decoration: none;
  border-radius: 5px;
}
.s_h{
  display: none;
}
.bottom_instra
{
  max-width: 750px;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  /* height: 100px; */
}
.lolty{
  min-width: 750px;
}
.collored{
  background: #5c52ff  !important;
}
.winner
{
  flex-direction: column;
  /* background-color: #25ffbe; */
  display: flex;
  }
.prev-button, .next-button {
  width: 80px;
  height: 40px;
  border-radius: 5px;
  border: none;
  background-color: #c3c782;
}
#formi{
    display: flex;
    flex-wrap: nowrap;
    justify-content: center;
}
#formi > label, input, button {
    align-self: center; 
  margin: 5px;
}
#formi > button {
    width: 102px;
    height: 39px;
    padding: 12px;
    border: none;
    border-radius: 5px;
    background-color: #f6f07da8;
    color: black;
  }

  #instrac{
    width: 20%;
    display: flex;
    margin-right: -5%;
  }
.formi2{
  margin-top: 90px;
  display: flex;
  flex-direction: column;
    margin-left: 45px;
  }
#formi1{
    /* display: flex;
    flex-direction: column;
    justify-content: center; */
    margin-top: 50px;
    min-width: 165px;
    margin-left: 45px;
}
#formi1 > label, input, button {
    align-self: center; 
  margin: 5px;
}
#formi1 >  input {
  height: 250px;
  /* cursor: pointer; */
}
#formi1 > button {
    width: 102px;
    height: 39px;
    padding: 12px;
    border: none;
    border-radius: 5px;
    background-color: #f6f07da8;
    color: black;
  }
  textarea {
    width: 100%; /* or any other desired width */
    padding: 12px 20px;
    margin: 8px 0;
    box-sizing: border-box;
    border: 2px solid #ccc;
    border-radius: 4px;
    background-color: #f8f8f8;
    font-size: 16px;
    /* resize: none; to prevent resizing of the textarea */
}

textarea:focus {
    border: 2px solid #555;
}

.for_nmb {
  width: 30%;
}
.for_ens {
  width: 100%;
  min-height: 250px;
  min-width: 120px;
  max-width: 180px;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.stack-a {
  /* background: #ffffff; */
  margin: 10px;
  width: 50px;
  display: flex;
  flex-direction: column-reverse;
  justify-content: flex-end;
}

.stack-b {
  /* background: #fff; */
  margin: 10px;
  width: 50px;
  display: flex;
  flex-direction: column-reverse;
  justify-content: flex-end;
}

.stack-a .n-item {
  background: #fdfffe;
}

.stack-b .n-item {
  background: #ffffff;
}

.n-item {
  height: 50px;
  width: 50px;
  line-height: 50px;
  box-shadow: 1px 1px 3px #00000038;
  font-weight: 900;
}
.swipe {
  background: #2bafee;
  border: 0;
  outline: 0;
  height: 50px;
  width: 50px;
  /* border-top: 2px solid #fff; */
  /* border-bottom: 2px solid #fff; */
  font-weight: 900;
  margin: auto;
}
.push-rrb
{
  border-radius: 4px;
}
.push-rr
{
  border-radius: 4px;
}
.instra {
  background: #000;
  color: #FFF;
  height: 50px;
  width: 50px;
  line-height: 50px;
  display: inline-block;
  font-weight: 900;
}

.btn {
  background: rgb(255, 255, 255);
  border: 0;
  outline: 0;
  height: 50px;
  width: 150px;
  border-top: 2px solid #ccc;
  border-bottom: 2px solid #ccc;
  font-weight: 900;
  margin: 8px 100px;
  border-radius: 7px;
}
</style>

