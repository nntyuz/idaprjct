<template>
  <div class="filters-component">
    <div class="input-item required">
      <div class="title flex">Наименование товара</div>
      <input
        v-model="name"
        type="text"
        placeholder="Введите наименование товара"
      />
    </div>

    <div class="input-item">
      <div class="title flex">Описание товара</div>
      <textarea
        v-model="description"
        placeholder="Введите описание товара"
      ></textarea>
    </div>

    <div class="input-item required">
      <div class="title flex">Ссылка на изображение товара</div>
      <input
        v-model="img"
        type="url"
        placeholder="Введите наименование товара"
      />
    </div>
    <div class="input-item required">
      <div class="title flex">Цена товара</div>
      <input v-model="price" type="number" placeholder="Введите цену товара" />
    </div>
    <button :disabled="!enable" class="add-button" @click="add">
      Добавить товар
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: null,
      description: null,
      img: null,
      price: null,
    }
  },
  computed: {
    enable() {
      return this.name && this.img && this.price
    },
  },
  methods: {
    add() {
      if (!this.enable) {
        return
      }

      this.$emit('add', {
        name: this.name,
        img: this.img,
        description: this.description,
        price: this.price,
      })
    },
  },
}
</script>

<style lang="scss" scoped>
.filters-component {
  width: 332px;
  flex-shrink: 0;
  align-self: start;
  padding: 24px;
  border-radius: 4px;
  background-color: #fffefb;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);

  .input-item {
    margin-bottom: 16px;
    &:last-child {
      margin-bottom: 24px;
    }
    &.required {
      .title::after {
        content: '';
        align-self: start;
        width: 4px;
        height: 4px;
        background-color: #ff8484;
        border-radius: 100%;
      }
    }

    input {
      width: 100%;
      height: 36px;
      padding-left: 16px;
      border: none;
      border-radius: 4px;
      font-size: 12px;
      line-height: 15px;
      background-color: #fffefb;
      color: #b4b4b4;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      &.error {
        border: 1px solid red;
      }
      &:focus {
        outline: none;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
      }
    }

    textarea {
      width: 100%;
      height: 125px;
      padding-top: 10px;
      padding-left: 16px;
      background: #fffefb;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      border: none;
      resize: none;
      border-radius: 4px;
      &:focus {
        outline: none;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
      }
    }
  }

  .title {
    font-size: 10px;
    line-height: 13px;
    letter-spacing: -0.02em;
    color: #49485e;
    margin-bottom: 4px;
  }

  .add-button {
    font-family: 'Inter', Arial, Helvetica, sans-serif;
    width: 100%;
    height: 36px;
    align-items: center;
    justify-content: center;
    border-radius: 10px;
    font-weight: 600;
    font-size: 12px;
    line-height: 15px;
    letter-spacing: -0.02em;
    background-color: #7bae73;
    color: white;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    cursor: default;
    &[disabled] {
      color: #b4b4b4;
      background-color: #eee;
    }
    &:not([disabled]) {
      cursor: pointer;
      &:hover {
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
      }
      &:active {
        opacity: 0.8;
      }
    }
  }
}
@media (max-width: 960px) {
  .filters-component {
    width: 100%;
    margin-bottom: 24px;
  }
}
</style>
