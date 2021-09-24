<template>
  <div>
    <p>{{datas}}</p>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data: function() {
    return {
       datas: undefined
    };
  },
  created() {
    this.setupStream();
  },
  methods: {
    setupStream(){
      let es = new EventSource('http://localhost:8080/stream-sse')
      es.addEventListener('periodic-event', event => {
        this.datas = event.data;
      }, false)
    }
  }

}
</script>
