<template>
  <h1>hello {{ name }}</h1>
  <div v-text="channel"></div>
  <div v-html="withHtml"> </div>
  <div :id="headingId"> </div>
  <button :disabled="isDisabled">click me</button>
  <h2 :class="status" class="underline"> firefox </h2>
  <h2 :class="isPromoted && 'promoted'" class="underline"> movie </h2>
  <h2 :class="isSoldout ? 'soldout' : 'new'" > soldout </h2>
  <h2 :class="['new','promoted']" > array classes </h2>
  <h2 :class="[isSoldout ? 'soldout' : 'new', isPromoted && 'promoted']" > array classes </h2>


  <h2 :class="{
  promoted: isPromoted,
  new: !isSoldout,
  'soldout': isSoldout
  }"> object conditional </h2>

  <h2 :style="{
  color: highlighColor,
  'font-size': hfontsize + 'px',
  fontStyle: hfontstyle,
  padding: '20px'
  }"> Inline Style Binding Styles</h2>

  <h2 :style="headerStyleobject">header style objects</h2>

  <div :style="[arrayStyleobject01, arrayStyleobject02]">array style</div>

  <div v-if="num == 5">this number is five</div>
  <div v-else-if="num == 0">this number is zero</div>
  <div v-else>this number is not five</div>

  <template v-if="display">
    <h4>vishwas</h4>
    <h4>code evo</h4>
    <h4>2.0</h4>
  </template>

  <div v-show="showElement">using v-show </div>
  <div v-if="showElement">using v-f </div>

  <hr>
  <template v-if="display">
  <div>
    <ul v-for="(n, i) in names" :key="n">
      <li> {{ i }} - {{ n }}</li>
    </ul>

    <ul v-for="(n, i) in fullNames" :key="n">
      <li> {{ i }} - {{ n.firstname }} {{ n.lastname }}</li>
    </ul>
  </div>
  </template>

  <hr>
  <h3>Accessing objects in array</h3>
  <div v-for="actor in actors" :key="actor.name">
    <h3> {{ actor.name}}</h3>
    <ul v-for="movie in actor.movies" :key="movie">
      <li> {{ movie }}</li>
    </ul>
  </div>
  
  <hr />
  <h3>Accessing objects</h3>
  <div v-for="value,key,index in myinfo" :key="value">
    <div>{{ index }} - {{ key }} - {{ value }}</div>
  </div>

  <hr />
  <h3>Conditional List Rendering</h3>
  <div v-for="value,key,index in marvelHeros" :key="value" >
    <div v-if="value == 'spiderman'">{{ index }} - {{ key }} - {{ value }}</div>
  </div>

  <hr />
  <h3>Methods</h3>
  <div>{{ addIt(5,10+1,15) }}</div>
  <div>{{ addIt(1,2,3+4) }}</div>
  <div>{{ multiplyIt(3) }}</div>
  <div>{{ multiplyIt(baseValue) }}</div>

  <hr />
  <h3>Event Handling (Part 1)</h3>
  <div>
    onkeyup: <input type="text" ref="myInput" @keyup="changeName(getInputValue())"><br/>
    <button @click="changeName(getInputValue())"> change name</button> <br/>
    <button @mouseover="changeName('batman')"> change name to batman (mouseover)</button><br/>
    <div>
      {{ myname01 }}
    </div>
  </div>
  <div>
    <div>Counter</div>
    <button @click="myCounter('-')">-</button>{{ myCount }}<button @click="myCounter('+')">+</button> <br>
    
  </div>

  <hr />
  <h3>Event Handling (Part 2)</h3>
    <button @click="myCounter02(1, $event)">event log</button> <br>
    {{ (myCount < 0) ? 'counter already negative' : '' }}<br>

    <button @click="myCounter('+'), changeName('added +1')">increment + change name (multiple event handlers)</button>
  <div></div>

  <hr />
  <h3>Form Handling</h3>
  <div>
    <div class="container">
      <div>
        {{ JSON.stringify(myFormValues, null, 2)}}
      </div>
      
      <form @submit="submitMyApplication">
        <label for="fname">First Name</label>
        <input type="text" id="fname" name="fname" placeholder="Your name.." v-model="myFormValues.fname">

        <label for="lname">Last Name</label>
        <input type="text" id="lname" name="lname" placeholder="Your last name.." v-model="myFormValues.lname">

        <label for="country">Country</label>
        <select id="country" name="country" v-model="myFormValues.country">
          <option value="ph">Philippines</option>
          <option value="vet">Vietnam</option>
          <option value="sg">SG</option>
        </select>

        <label for="jobLocation">Job Location</label>
        <select id="jobLocation" name="jobLocation" v-model="myFormValues.jobLocation" multiple>
          <option value="australia">Australia</option>
          <option value="canada">Canada</option>
          <option value="usa">USA</option>
        </select>

        <label for="summary">Summary</label>
        <textarea id="profileSummary" name="profileSummary" placeholder="Write something.." style="height:200px" v-model="myFormValues.profileSummary"></textarea>

        
        <input type="checkbox" id="remoteWork" name="remoteWork" placeholder="Your last name.." 
          v-model="myFormValues.remoteWork"
          true-value="yes"
          false-value="no"
        >
        

        <div class="skillsets">
          <label for="remoteWork">Remote Work</label>
          <div class="eachbox"><input type="checkbox" id="mySkills" value="html" v-model="myFormValues.mySkills"><span>HTML </span></div>
          <div class="eachbox"><input type="checkbox" id="mySkills" value="css" v-model="myFormValues.mySkills"><span>CSS </span></div>
          <div class="eachbox"><input type="checkbox" id="mySkills" value="javascript" v-model="myFormValues.mySkills"><span>Javascript </span></div>
        </div>

        <div>
          <h4>Years of Experience</h4>
         
          <input type="radio" id="html" value="0-2" v-model="myFormValues.yearsOfExperience"> <label for="0-2">0-2</label>
          <input type="radio" id="html" value="3-5" v-model="myFormValues.yearsOfExperience"> <label for="3-5">3-5</label>
          <input type="radio" id="html" value="6-10" v-model="myFormValues.yearsOfExperience"> <label for="6-10">6-10</label>
          <input type="radio" id="html" value="10+" v-model="myFormValues.yearsOfExperience"> <label for="10+">10+</label>
        </div>

        <input type="submit" value="Submit">
      </form>
    </div>
  </div>

</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      name: 'val caro',
      channel: 'halows!',
      withHtml: "<b> code evolution</b>",
      headingId: 'heading',
      isDisabled: true,
      status: 'warning',
      isPromoted: true,
      isSoldout: true,
      highlighColor: 'orange',
      hfontsize: 50,
      hfontstyle: 'italic',
      headerStyleobject: {
        color: 'cyan',
        fontSize: '40px',
        fontStyle: 'italic',
        padding: '20px'
      },
      arrayStyleobject01: {
        fontSize: '30px',
        padding: '5px'
      },
      arrayStyleobject02: {
        color: 'white',
        fontStyle: 'normal',
        backgroundColor: 'green',
        border: '1px solid black'
      },
      num: 0,
      display: true,
      showElement: true,
      names: ['bruce', 'clark', 'diana'],
      fullNames: [
        {firstname: 'axl', lastname: 'good job!'},
        {firstname: 'axl2', lastname: 'good job2'},
        {firstname: 'axl3', lastname: 'good job2'},
      ],
      actors: [
        {
          name: 'christian bale',
          movies: ['batman', 'superman']
        },
        {
          name: 'di carpio',
          movies: ['titanic', 'inception']
        }
      ],
      myinfo: {
        name: 'vcaro',
        channel: 'youtube',
        github: 'okies'
      },
      marvelHeros: ['dr strange', 'spiderman', 'ironman'],
      baseMultiplier: 5,
      baseValue: 3,
      myname01: 'val axl grey',
      myCount: 0,
      myFormValues: {
        fname: '',
        lname: '',
        profileSummary: '',
        country: '',
        jobLocation: [],
        remoteWork: 'no',
        mySkills: [],
        yearsOfExperience: '0-2'
      },
      
    }
  },
  methods: {
    addIt(a,b,c) {
      return a+b+c
    },
    multiplyIt(num) {
      return num * this.baseMultiplier
    },
    changeName(myname) {
      return this.myname01 = myname
    },
    myCounter(operator) {
      if(operator == '-') {
        this.myCount -= 1
      }else {
        this.myCount += 1
      }
    },
     myCounter02(num, event) {
      console.log("🚀 ~ myCounter02 ~ event", event)
    },
    getInputValue() {
      return this.$refs.myInput.value
    },
    submitMyApplication(event) {
      event.preventDefault();
      console.log(this.myFormValues)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.underline {
  text-decoration: underline;
}

.warning {
  background-color: red;
  color: white;
}

.promoted {
  font-style: italic;
}

.soldout {
  background-color: brown;
  color: white;
  font-style: italic;
  text-transform: uppercase;
  text-decoration: line-through;
}

.new {
  background-color: yellow;
  color: black;
}

input[type=text], select, textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

input[type=submit] {
  background-color: #04AA6D;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}

.container {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}

.skillsets .eachbox{
  display: block;
}
.skillsets input{
  display: inline-block;
}
.skillsets span{
  display: inline-block;
}
</style>
