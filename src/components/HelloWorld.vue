<template>
  <div class="hello">
    <div class="columns  is-multiline">
      <div class="column is-one-third">
        <button class="button is-info" @click="addObjeto">Add new</button>
      </div>
      <div class="column is-one-third" v-for="(ob,key) in objetos" :key="key">
        <section>
          <div class="card">
            <header class="card-header">
              <p class="card-header-title">
                Component
              </p>
              <button
                class="card-header-icon"
                aria-label="more options"
                @click="ob.show = !ob.show"
              >
                <span class="icon">
                  <i class="fas fa-angle-down" aria-hidden="true"></i>
                </span>
                <span class="text">{{ ob.show ? 'Hide' : 'Show' }}</span>
              </button>
            </header>
            <div v-show="ob.show">
              <transition name="fade" mode="out-in">
                <div class="card-content">
                  <div class="content">
                    {{ob.email}}
                    <input type="email" v-model="ob.email" name="" id="">
                    <a href="#">@bulmaio</a>. <a href="#">#css</a> <a href="#">#responsive</a>
                    <br>
                    <time datetime="2016-1-1">11:09 PM - 1 Jan 2016</time>
                  </div>
                </div>
              </transition>
              <footer class="card-footer">
                <a href="#" class="card-footer-item">Save</a>
                <a href="#" class="card-footer-item">Edit</a>
                <a @click="deleteObjeto(key)" class="card-footer-item">Delete</a>
              </footer>
            </div>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      objetos: [
        { show: false },
        { show: false },
        { show: false },
      ],
    };
  },
  methods: {
    addObjeto() {
      this.$set(this.objetos, this.objetos.length, { show: false });
    },
    deleteObjeto(index) {
      this.objetos.splice(index, 1);
    },
  },
};
</script>
