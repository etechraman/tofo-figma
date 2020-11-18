<template>
  <div>
    <transition name="modal">
      <div class="modal-mask">
        <div class="modal-wrapper">
          <div class="modal-container">
            <div>
              <form>
                <label>Add Todo</label>
                <br />
                <textarea rows="11" v-model="todo" required></textarea>
                <br />
                <p id="cancel" @click="close">Cancel</p>
                <p id="done" @click.prevent="submit">Done</p>
              </form>
            </div>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "Form",
  data: function() {
    return {
      todo: "",
    };
  },

  methods: {
    submit() {
      if (this.todo == "") {
        return alert("Nothing to add");
      }
      this.$emit("submitItem", this.todo);
      this.close();
    },
    close() {
      this.$emit("close");
    },
  },
};
</script>

<style>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.modal-wrapper {
  margin-top: 110px;
}

.modal-container {
  height: 260px;
  width: 78%;
  margin: auto;
  padding-left: 15px;
  padding-right: 15px;
  padding-top: 12px;
  background-color: #fff;
  border-radius: 10px;
  border: 1px solid #ebeff5;
  transition: all 0.3s ease;
}

#cancel {
  float: left;
  margin-top: 10px;
  margin-left: 11px;
  font-family: SFProText;
  font-style: normal;
  font-weight: normal;
  font-size: 18px;
  line-height: 21px;
  letter-spacing: -0.434118px;
  color: #006cff;
}
#cancel:hover {
  cursor: pointer;
}

#done {
  margin-top: 10px;
  margin-left: 93%;
  font-family: SFProText;
  font-style: normal;
  font-weight: 600;
  font-size: 18px;
  line-height: 21px;
  letter-spacing: -0.434118px;
  color: #006cff;
}
#done:hover {
  cursor: pointer;
}

textarea {
  border-radius: 10px;
  width: 100%;
  resize: none;
  border: 1px solid #ebeff5;
  box-sizing: border-box;
}

label {
  font-family: SFProText;
  font-size: 18px;
  line-height: 41px;
  letter-spacing: 0.01em;
  color: #000000;
}
@media screen and (max-width: 900px) {
  #done {
    margin-left: 90%;
  }
}

@media screen and (max-width: 710px) {
  #done {
    margin-left: 87%;
  }
}

@media screen and (max-width: 600px) {
  #done {
    margin-left: 85%;
  }
}

@media screen and (max-width: 450px) {
  #done {
    margin-left: 80%;
  }
}
</style>
