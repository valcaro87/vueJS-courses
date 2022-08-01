<template>
  <h1> {{ username }}</h1>
  <h3>hello {{ name }}</h3>
  <div v-text="channel"></div>
  <div v-html="withHtml"> </div>
  <div :id="headingId"> </div>
  <button :disabled="isDisabled">click me</button>
  <h2 :class="status" class="underline"> firefox </h2>
  <h2 :class="isPromoted && 'promoted'" class="underline"> movie </h2>
  <h2 :class="isSoldout ? 'soldout' : 'new'"> soldout </h2>
  <h2 :class="['new', 'promoted']"> array classes </h2>
  <h2 :class="[isSoldout ? 'soldout' : 'new', isPromoted && 'promoted']"> array classes </h2>


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
    <h3> {{ actor.name }}</h3>
    <ul v-for="movie in actor.movies" :key="movie">
      <li> {{ movie }}</li>
    </ul>
  </div>

  <hr />
  <h3>Accessing objects</h3>
  <div v-for="value, key, index in myinfo" :key="value">
    <div>{{ index }} - {{ key }} - {{ value }}</div>
  </div>

  <hr />
  <h3>Conditional List Rendering</h3>
  <div v-for="value, key, index in marvelHeros" :key="value">
    <div v-if="value == 'spiderman'">{{ index }} - {{ key }} - {{ value }}</div>
  </div>

  <hr />
  <h3>Methods</h3>
  <div>{{ addIt(5, 10 + 1, 15) }}</div>
  <div>{{ addIt(1, 2, 3 + 4) }}</div>
  <div>{{ multiplyIt(3) }}</div>
  <div>{{ multiplyIt(baseValue) }}</div>

  <hr />
  <h3>Event Handling (Part 1)</h3>
  <div>
    onkeyup: <input type="text" ref="myInput" @keyup="changeName(getInputValue())"><br />
    <button @click="changeName(getInputValue())"> change name</button> <br />
    <button @mouseover="changeName('batman')"> change name to batman (mouseover)</button><br />
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
    <h3>Directives - v-once v-pre</h3>
    <div>
      <span v-once>{{ testingVonce }} </span>
      <button @click="testingVonce = 'superman'"> v-once cant modify </button><br />
      <span v-pre>{{ testingVonce}} </span>
    </div>

    <hr />
    <h3>Form Handling</h3>
    <div>
      <div class="app-container">
        <div>
          {{ JSON.stringify(myFormValues, null, 2) }}
        </div>

        <!-- modifiers: .trim .number lazy .prevent    -->
        <form @submit.prevent="submitMyApplication">
          <label for="fname">First Name</label>
          <input type="text" id="fname" name="fname" placeholder="Your name.." v-model.trim.lazy="myFormValues.fname">

          <label for="lname">Last Name</label>
          <input type="text" id="lname" name="lname" placeholder="Your last name.." v-model="myFormValues.lname">

          <label for="age">Age</label>
          <input type="text" id="age" name="age" placeholder="age" v-model.number="myFormValues.age">

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
          <textarea id="profileSummary" name="profileSummary" placeholder="Write something.." style="height:200px"
            v-model="myFormValues.profileSummary"></textarea>


          <input type="checkbox" id="remoteWork" name="remoteWork" placeholder="Your last name.."
            v-model="myFormValues.remoteWork" true-value="yes" false-value="no">


          <div class="skillsets">
            <label for="remoteWork">Remote Work</label>
            <div class="eachbox"><input type="checkbox" id="mySkills" value="html"
                v-model="myFormValues.mySkills"><span>HTML </span></div>
            <div class="eachbox"><input type="checkbox" id="mySkills" value="css"
                v-model="myFormValues.mySkills"><span>CSS </span></div>
            <div class="eachbox"><input type="checkbox" id="mySkills" value="javascript"
                v-model="myFormValues.mySkills"><span>Javascript </span></div>
          </div>

          <div>
            <h4>Years of Experience</h4>

            <input type="radio" id="html" value="0-2" v-model="myFormValues.yearsOfExperience"> <label
              for="0-2">0-2</label>
            <input type="radio" id="html" value="3-5" v-model="myFormValues.yearsOfExperience"> <label
              for="3-5">3-5</label>
            <input type="radio" id="html" value="6-10" v-model="myFormValues.yearsOfExperience"> <label
              for="6-10">6-10</label>
            <input type="radio" id="html" value="10+" v-model="myFormValues.yearsOfExperience"> <label
              for="10+">10+</label>
          </div>

          <!-- <input type="submit" value="Submit"> -->
          <input @keyup.enter.prevent="submitMyApplication" type="text" id="submitWhenEnter"
            v-model.number="myFormValues.submitWhenEnter">


        </form>
      </div>
    </div>

    <hr />
    <h3>Computed Properties (recalculated when dependencies changed)</h3>
    <div>
      {{ fullName }}
    </div>
    <div>
      Total Cart Amount: {{ totalCartAmount }} <br>

      <button @click="cartItems.push({ id: 4, item: 'monitor', price: 49000 })"> Add Item</button>

    </div>

    <hr />
    <h3>Computed Properties vs. Methods</h3>
    <div>
      Methods are "expensive" processes
      always called when there is changed in the UI
      Total Cart Amount (method): {{ totalCartAmount02() }} <br>
      <input type="text" v-model="name">
    </div>

    <hr />
    <h3>Computed Properties and v-for</h3>
    <div>

      <ul v-for="item in cartItems" :key="item.id">
        <li> {{ item.id }}</li>
        <li> {{ item.item }}</li>
        <li> {{ item.price }}</li>
      </ul>
      <h4>Expensive Items</h4>
      <ul v-for="item in expensiveItems" :key="item.id">
        <li> {{ item.id }}</li>
        <li> {{ item.item }}</li>
        <li> {{ item.price }}</li>
      </ul>
      <button @click="cartItems.push({ id: 5, item: 'car', price: 1490000 })"> Add Expensive Item</button>
    </div>

    <hr />
    <h3>Computed Setters</h3>
    <div>
      <button @click="changeFullname">Change Full Name</button>
      {{ myFullname }}
    </div>

    <hr />
    <h3>Watchers</h3>
    <div>Volume Tracker (0-20)</div>
    <div>Current Volume: {{ volume }} -- {{ volumeAlert }} <br>
      <button @click="volume -= 1" :disabled="volume <= 0 ? true : false"> - </button>
      <button @click="volume += 1" :disabled="volume == 10 ? true : false"> + </button>
    </div>

    <hr />
    <h3>Immediate and Deep Watchers</h3>
    <div>
      {{ mymovie }}
      <br>
      <input type="text" v-model.lazy="mymovie">
      <br>
      <input type="text" v-model="movieInfo.title">
      <input type="text" v-model="movieInfo.actor">
      <br>
      {{ movieList }}
      <button @click="movieList.push('wonderwoman')">add Movie to list</button>
    </div>

    <hr />
    <h3>Components</h3>
    <GreetComp more-Name="bruce" hero-Name="iron man" />
    <GreetComp more-Name="diana" hero-Name="hulk" />
    <GreetComp more-Name="john doe" />
    <GreetComp :more-Name="myfirstName" :hero-Name="mylastName" />

    <hr />
    <h3>Prop Types and Validations</h3>
    <ArticleComp title="Rails 2022" :likes="13" :isPublished="isPromoted" />

    <hr />
    <h3>Non Prop Attributes</h3>
    <ArticleComp id="my-article" title="Rails 2022" :likes="13" :isPublished="isPromoted" />

    <CccComp />

    <hr />
    <h3>Component Events / Validating Emitted Events</h3>
    <button @click="popupShow = true, popupShowMessage = ''" v-show="!popupShow"> [/] show popup</button>
    <div>{{ popupShowMessage }}</div>
    <PopupComp v-show="popupShow" @closePopup="closethisPopup" />

    <hr />
    <h3>Components and v-model</h3>
    <div>
      <InputComp v-model="cars" />
      your input: {{ cars }}
    </div>

    <hr />
    <h3>Slots (parent controlling child component) / Card Component / Named Slots</h3>
    <div>

      <CardComp :employees="employees">

        <template v-slot:header>
          header
        </template>

        <template v-slot:image>
          <img src="https://www.w3schools.com/howto/img_avatar.png" alt="Avatar" style="width:100%">
        </template>

        <template v-slot:footer>
          <button> View Employee </button>
        </template>

      </CardComp>
    </div>


    <hr />
    <h3>Slots Props</h3>
    <NameListComp>
      <template v-slot:default="slotProps">
        {{ slotProps.actorFname }} - {{ slotProps.actorLname }}
      </template>
    </NameListComp>

    <NameListComp>
      <template v-slot:default="slotProps">
        {{ slotProps.actorLname }}, {{ slotProps.actorFname }}
      </template>
    </NameListComp>


    <hr />
    <h3>Components Styles</h3>
    <ChildStyles>
      <h4>Child Styles Component</h4>
    </ChildStyles>

    <hr />
    <h3>Dynamic Components (Tabs) / Keeping Dynamic Components Alive</h3>
    <button @click="activeTab = 'TabA'">Tab A</button>
    <button @click="activeTab = 'TabB'">Tab B</button>
    <button @click="activeTab = 'TabC'">Tab C</button>

    <keep-alive>
      <component :is="activeTab" />
    </keep-alive>
    <!-- this will reduce the amount of code and easy to maintain in the long run -->
    <!-- <TabA v-if="activeTab === 'TabA'" />
    <TabB v-if="activeTab === 'TabB'" />
    <TabC v-if="activeTab === 'TabC'" /> -->


    <!-- Teleport Component -->
    <PortalComp />

    <hr />

    <button @click="showModal = true">Show Modal</button>
    <teleport to="#modal-root">
      <ModalComp v-show="showModal" @closeModal="showModal = false" title="Vue + Rails 2023">

        <template v-slot:defaultClass>
          Popup Modal Content
        </template>

        <template v-slot:modalcontentSlotOption>
          some questions here
        </template>
      </ModalComp>
    </teleport>

</template>

<script>
import GreetComp from './components/Greet.vue'
import ArticleComp from './components/Article.vue'
import CccComp from './components/Ccc.vue'
import PopupComp from './components/Popup.vue'
import InputComp from './components/Input.vue'
import CardComp from './components/Card.vue'
import NameListComp from './components/NameList.vue'
import ChildStyles from './components/ChildStyles.vue'
import TabA from './components/tabs/A.vue'
import TabB from './components/tabs/B.vue'
import TabC from './components/tabs/C.vue'
import PortalComp from './components/Portal.vue'
import ModalComp from './components/Modal.vue'


export default {
  name: "App",
  components: {
    GreetComp,
    ArticleComp,
    CccComp,
    PopupComp,
    InputComp,
    CardComp,
    NameListComp,
    ChildStyles,
    TabA,
    TabB,
    TabC,
    PortalComp,
    ModalComp,
  },
  data() {
    return {
      showModal: false,
      username: 'valcaro87@gmail.com',
      name: "val caro",
      channel: "halows!",
      withHtml: "<b> code evolution</b>",
      headingId: "heading",
      isDisabled: true,
      status: "warning",
      isPromoted: true,
      isSoldout: true,
      highlighColor: "orange",
      hfontsize: 50,
      hfontstyle: "italic",
      headerStyleobject: {
        color: "cyan",
        fontSize: "40px",
        fontStyle: "italic",
        padding: "20px"
      },
      arrayStyleobject01: {
        fontSize: "30px",
        padding: "5px"
      },
      arrayStyleobject02: {
        color: "white",
        fontStyle: "normal",
        backgroundColor: "green",
        border: "1px solid black"
      },
      num: 0,
      display: true,
      showElement: true,
      names: ["bruce", "clark", "diana"],
      fullNames: [
        { firstname: "axl", lastname: "good job!" },
        { firstname: "axl2", lastname: "good job2" },
        { firstname: "axl3", lastname: "good job2" },
      ],
      actors: [
        {
          name: "christian bale",
          movies: ["batman", "superman"]
        },
        {
          name: "di carpio",
          movies: ["titanic", "inception"]
        }
      ],
      myinfo: {
        name: "vcaro",
        channel: "youtube",
        github: "okies"
      },
      marvelHeros: ["dr strange", "spiderman", "ironman"],
      baseMultiplier: 5,
      baseValue: 3,
      myname01: "val axl grey",
      myCount: 0,
      myFormValues: {
        fname: "",
        lname: "",
        age: null,
        profileSummary: "",
        country: "",
        jobLocation: [],
        remoteWork: "no",
        mySkills: [],
        yearsOfExperience: "0-2",
        submitWhenEnter: null
      },
      testingVonce: "batman",
      cartItems: [
        {
          id: 1,
          item: "phone",
          price: 200
        },
        {
          id: 2,
          item: "laptop",
          price: 145000
        },
        {
          id: 3,
          item: "desktop",
          price: 105000
        }
      ],
      myfirstName: "clark",
      mylastName: "kent",
      volume: 0,
      volumeAlert: "",
      mymovie: "netflix",
      movieInfo: {
        title: "",
        actor: ""
      },
      movieList: ["the revenant", "up"],
      popupShow: false,
      popupShowMessage: '',
      cars: "",
      employees: [
        {
          name: 'John Doe',
          title: 'IT Consultant',
        },
        {
          name: 'Mary Smith',
          title: 'HR Manager'
        }
      ],
      activeTab: 'TabA'
    }
  },
  methods: {
    addIt(a, b, c) {
      return a + b + c;
    },
    multiplyIt(num) {
      return num * this.baseMultiplier;
    },
    changeName(myname) {
      return this.myname01 = myname;
    },
    myCounter(operator) {
      if (operator == "-") {
        this.myCount -= 1;
      }
      else {
        this.myCount += 1;
      }
    },
    myCounter02(num, event) {
      console.log("🚀 ~ myCounter02 ~ event", event);
    },
    getInputValue() {
      return this.$refs.myInput.value;
    },
    submitMyApplication() {
      // event.preventDefault();
      console.log(this.myFormValues);
    },
    totalCartAmount02() {
      console.log("🚀 ~ totalCartAmount ~ method property");
      return this.cartItems.reduce((total, x) => (total += x.price), 0)
    },
    changeFullname() {
      this.myFullname = "spider man"
    },
    closethisPopup(message) {
      this.popupShow = false
      this.popupShowMessage = message
    }
  },
  computed: {
    fullName() {
      return `hallows! ${this.name}`;
    },
    totalCartAmount() {
      console.log("🚀 ~ totalCartAmount ~ computed");
      return this.cartItems.reduce((total, x) => (total += x.price), 0);
    },
    expensiveItems() {
      return this.cartItems.filter(item => item.price > 100000);
    },
    //setter //getter
    myFullname: {
      get() {
        return `${this.myfirstName} ${this.mylastName}`;
      },
      set(value) {
        const names = value.split(" ");
        this.myfirstName = names[0];
        this.mylastName = names[1];
      }
    },
  },
  watch: {
    volume(newVolumValue, oldVolumValue) {
      if (newVolumValue > oldVolumValue && newVolumValue == 7) {
        this.volumeAlert = "High volume alert";
      }
      else {
        this.volumeAlert = "";
      }
    },
    // mymovie(newMovieValue) {
    //   console.log `calling API from ${newMovieValue}`
    // }
    mymovie: {
      handler(newMovieValue) {
        console.log`calling API from ${newMovieValue}`;
      },
      immediate: true,
    },
    movieInfo: {
      handler(newValue) {
        console.log`calling API from ${newValue.title} - ${newValue.actor}`;
      },
      immediate: true,
      deep: true //deep nested object
    },
    movieList: {
      handler(newValue) {
        console.log`calling API from ${newValue}`;
      },
      deep: true
    }
  },
  provide() {
    return { username: this.username } // provide - inject to component Fff
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

input[type=text],
select,
textarea {
  width: 20%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
  display: block;
  margin: 0 auto;
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

.app-container {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}

.skillsets .eachbox {
  display: block;
}

.skillsets input {
  display: inline-block;
}

.skillsets span {
  display: inline-block;
}

h4 {
  color: blue;
}

/* .container {
  height: 100%;
  display: grid;
  justify-content: center;
  align-items: center;
} */

/* .content {
  max-width: 400px;
  position: relative;
} */
</style>
