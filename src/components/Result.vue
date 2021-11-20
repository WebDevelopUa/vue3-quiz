<template>
  <div class="result">
    <div class="title">
      {{ resultsProp[resultIndex].title }}
    </div>
    <div class="desc">
      {{ resultsProp[resultIndex].desc }}
    </div>

    <br/>
    <br/>
    <hr/>

    <div>
      <h3>App Data</h3>
      <p><strong>results.length:</strong> {{ resultsProp.length }}</p>
      <p><strong>results:</strong> {{ resultsProp }}</p>
    </div>


  </div>
</template>

<script>
export default {
  name: "Result",
  props: {
    resultsProp: {type: Object, required: true},
    totalCorrectProp: {type: Number, required: true}
  },
  // calculate and store the results
  computed: {
    resultIndex() {
      let index = 0;
      this.resultsProp.forEach((e, i) => {
        console.log(e)
        console.log(i)
        if (e.min <= this.totalCorrectProp && e.max >= this.totalCorrectProp) {
          index = i
        }
      })
      return index
    }
  }
}
</script>
