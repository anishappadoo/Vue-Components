<template>
  <button
    :style="{ 
fontSize: ppTextSize,
padding: ppTextPadding, 
color: dtTxtColor, 
backgroundColor: dtBgColor,
border: ppButtonBorder,
borderRadius: ppButtonBorderRadius,
fontFamily: ppFontFamily,
boxShadow: ppButtonShadow,
cursor: ppCursorIcon,
outline: ppButtonOutline,
textAlign: ppButtonTextAlign,
webkitTransitionDuration: ppButtonTransitionDuration,
transitionDuration: ppButtonTransitionDuration
}"
    @mouseover="fnSwapColors"
    @mouseleave="fnSwapColors"
    @click="ppClickFunction"
    :disabled="ppDisabled"
  >{{ ppText }}</button>
</template>

<script>
export default {
  data: function() {
    return {
      dtTxtColor: this.ppPrimaryColor,
      dtBgColor: this.ppSecondaryColor
    };
  },
  props: {
    ppText: {
      type: String,
      default: "Button",
      required: false
    },
    ppTextSize: {
      type: String,
      default: "15px",
      required: false
    },
    ppTextPadding: {
      type: String,
      default: "11px 20px",
      required: false
    },
    ppPrimaryColor: {
      type: String,
      default: "#000000",
      required: false
    },
    ppSecondaryColor: {
      type: String,
      default: "#ffffff",
      required: false
    },
    ppDisabledPrimaryColor: {
      type: String,
      default: "#bbbbbb",
      required: false
    },
    ppDisabledSecondaryColor: {
      type: String,
      default: "#eeeeee",
      required: false
    },
    ppButtonBorder: {
      type: String,
      default: "1px solid",
      required: false
    },
    ppButtonBorderRadius: {
      type: String,
      default: "4px",
      required: false
    },
    ppFontFamily: {
      type: String,
      default:
        "'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif",
      required: false
    },
    ppButtonShadow: {
      type: String,
      default: "none",
      required: false
    },
    ppCursorIcon: {
      type: String,
      default: "pointer",
      required: false
    },
    ppButtonOutline: {
      type: String,
      default: "none",
      required: false
    },
    ppButtonTextAlign: {
      type: String,
      default: "center",
      required: false
    },
    ppButtonTransitionDuration: {
      type: String,
      default: "0.2s",
      required: false
    },
    ppClickFunction: {
      type: Function,
      default: function() {},
      required: false
    },
    ppDisabled: {
      type: Boolean,
      default: false,
      required: false
    }
  },
  methods: {
    fnSwapColors: function() {
      let tempColor = this.dtTxtColor;
      this.dtTxtColor = this.dtBgColor;
      this.dtBgColor = tempColor;
    }
  },
  created: function() {
    if (this.ppDisabled == true) {
      this.dtTxtColor = this.ppDisabledPrimaryColor;
      this.dtBgColor = this.ppDisabledSecondaryColor;
    }
  },
  watch: {
    ppDisabled: function(val) {
      this.dtTxtColor =
        val == true ? this.ppDisabledPrimaryColor : this.ppPrimaryColor;
      this.dtBgColor =
        val == true ? this.ppDisabledSecondaryColor : this.ppSecondaryColor;
    }
  }
};
</script>