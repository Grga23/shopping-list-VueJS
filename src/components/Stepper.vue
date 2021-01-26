<template>
  <div>
    <md-steppers :md-active-step.sync="active" md-vertical md-linear v-show="done">
      <md-step id="first" md-label="First Step" md-description="Optional" :md-editable="true" :md-done.sync="first">
        <p>Select your regularly bought items in your 'Regular items' list, that you'd like to add to your 'Shopping list' for the next time</p>
        <md-button class="md-raised md-primary" @click="setDone('first', 'second')">Continue</md-button>
      </md-step>

      <md-step id="second" md-label="Second Step" :md-error="secondStepError" :md-editable="true" :md-done.sync="second">
        <p>Select items that that are low or out of stock and are bought on a monthly basis in your 'Monthly items' list. Selected items will be added to your 'Shopping list'</p>
        <md-button class="md-raised md-primary" @click="setDone('second', 'third')">Continue</md-button>
      </md-step>

      <md-step id="third" md-label="Third Step" :md-editable="false" :md-done.sync="third">
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias doloribus eveniet quaerat modi cumque quos sed, temporibus nemo eius amet aliquid, illo minus blanditiis tempore, dolores voluptas dolore placeat nulla.</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias doloribus eveniet quaerat modi cumque quos sed, temporibus nemo eius amet aliquid, illo minus blanditiis tempore, dolores voluptas dolore placeat nulla.</p>
        <md-button class="md-raised md-primary" @click="setDone('third', 'fourth')">Continue</md-button>
     </md-step>
     <md-step id="fourth" md-label="Fourth Step" :md-editable="false" :md-done.sync="fourth">
        <md-button class="md-raised md-primary" @click="setDone('third'), collapse()">Done</md-button>
      
      </md-step>
    </md-steppers>
  </div>
</template>

<script>
  export default {
    name: 'StepperNonEditable',
    data: () => ({
      active: 'first',
      first: false,
      second: false,
      third: false,
      secondStepError: null,
      done: true
    }),
    methods: {
      setDone (id, index) {
        this[id] = true

        this.secondStepError = null

        if (index) {
          this.active = index
        }
      },
      setError () {
        this.secondStepError = 'This is an error!'
      },
      
      collapse () {
        this.done = false
      }
    }
  }  
</script>


<style  scoped>
  .md-steppers {

  }

  #stepswrapper {
  width: 100%;
  height: auto%;
  border: 3px solid green;
  padding: 10px;
  margin: 0px;
}
 
li {
  color: green
}

</style>