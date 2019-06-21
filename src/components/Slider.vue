<template>
    <div class="slide">
      <div class="row card">
        <div class="column">
          <slot name="media"></slot>
        </div>
        <div class="column">
          <slot name="text"></slot>
          <slot name="text1"></slot>
        </div>
      </div>
        <!-- <slot name="test2"></slot> -->
    </div>
</template>
<script>
export default{
  name: 'slider',
  data () {
    return {
      elementWidth: 0
    }
  },
  props: [
    'slide',
    'marginLeft', // ตัวหลัง- ในไฟล์slidesต้องตัวใหญ่
    'index',
    'clientWidth'
  ]
}
</script>

    <style scoped>

        *{
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        img{
             max-width: 100%;
             display: block;
             background-repeat: no-repeat;
             background-size: contain;
        }
        .slide{
            width: 400px;
            padding: 2px;
            display: inline-block;
        }
        .column {
          float: left;
          width: 50%;
        }

        .card{
          border: 1px solid rgba(0, 0, 0, 0.2);
          border-radius: 5px;
          overflow: hidden;
          box-shadow: 0 4px 4px 0 rgba(0, 0, 0, 0.2)
        }

        /* Clear floats after the columns */
        .row:after {
          content: "";
          display: table;
          clear: both;
        }
    </style>
