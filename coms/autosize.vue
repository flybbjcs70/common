<template>
  <div>
      <autosize-textarea :maxlength="maxlength" :placeholder="placeholder"  :handle-change="handleChange" :value="text"></autosize-textarea>
  </div>
</template>

<script>
import autosize from "autosize";

const AutosizeTextarea = {
  props: ["handle-change", "value", "placeholder", "maxlength"],
  template: `<textarea :maxlength="maxlength" :placeholder="placeholder"   class="autosize-textarea" @input="handleChange" >{{ value }}</textarea>`,
  mounted() {
    autosize(this.$el);
  }
};

export default {
  props: {
      placeholder: {
        type: String
      },
      maxlength: {
        type: Number
      },
      text: {
          type: String
      }
  },
  components: {
    AutosizeTextarea
  },
  data() {
    return {
    };
  },
  methods: {
    handleChange(e) {
      this.$emit('update:text',e.target.value)
      // this.text = e.target.value;
    }
  }
};
</script>

<style>
 .autosize-textarea {

  }

</style>
