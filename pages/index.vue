<template>
  <div class="main-container">
    <div class="header flex">
      <div class="title">Добавление товара</div>
      <button class="sort-button flex">
        По умолчанию
        <v-icon name="arrow-down" />
      </button>
    </div>
    <div class="wrapper flex">
      <Filters @add="add" />
      <div class="cards-container flex" tabindex="0">
        <div v-for="(product, index) in products" :key="index" class="card">
          <div class="card-img">
            <img :src="product.img" alt="Picture" />
          </div>
          <div class="card-container">
            <div class="card-title">{{ product.name }}</div>
            <div v-show="product.description" class="card-description">
              {{ product.description }}
            </div>
            <div class="card-price">{{ product.price }} руб.</div>
          </div>
          <button class="remove-button flex" @click="remove(product)">
            <v-icon name="bin" />
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Filters from '@/components/filters'
import vIcon from '@/components/ui/icon'

export default {
  components: {
    Filters,
    vIcon,
  },
  data() {
    return {
      products: [
        {
          name: 'Наименование товара',
          img: '/polaroid.png',
          description:
            'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
          price: '10 000',
        },
      ],
    }
  },
  methods: {
    add(product) {
      this.products.push(product)
    },
    remove(product) {
      this.products = this.products.filter((p) => p !== product)
    },
  },
}
</script>

<style lang="scss" scoped>
.main-container {
  max-width: 1440px;
  margin: 0 auto;
  padding: 0 15px;
  min-width: 375px;
}
.header {
  align-items: center;
  justify-content: space-between;
  margin-top: 32px;

  .title {
    font-weight: 600;
    font-size: 28px;
    line-height: 35px;
    color: #3f3f3f;
    @media (max-width: 680px) {
      font-size: 20px;
    }
  }
}
.sort-button {
  width: 120px;
  height: 36px;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  line-height: 15px;
  color: #b4b4b4;
  background-color: #fffefb;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  &:hover {
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  }
  &:active {
    opacity: 0.8;
  }
}
.sort-button svg {
  margin-left: 5px;
}
.wrapper {
  margin-top: 16px;

  @media (max-width: 960px) {
    flex-wrap: wrap;
  }
}
.cards-container {
  flex-grow: 1;
  flex-wrap: wrap;
  margin: 0 8px;
}
.remove-button {
  opacity: 0;
  position: absolute;
  top: -8px;
  right: -8px;
  width: 32px;
  height: 32px;
  align-items: center;
  justify-content: center;
  background: #ff8484;
  transition: 300ms ease;
  border-radius: 10px;
  svg {
    transition: 300ms ease;
    fill: #fff;
  }
  &:hover {
    background: #fff;
    svg {
      fill: #ff8484;
    }
  }
}
.card {
  display: flex;
  flex-direction: column;
  width: calc((100% - 48px) / 3);
  position: relative;
  margin: 0 8px;
  margin-bottom: 16px;
  border-radius: 4px;
  background-color: #fffefb;
  transition: 300ms ease;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04), 0 6px 10px rgba(0, 0, 0, 0.02);
  &:hover {
    box-shadow: 0 20px 30px rgba(0, 0, 0, 0.1), 0 6px 10px rgba(0, 0, 0, 0.05);
    .remove-button {
      opacity: 1;
    }
  }
  @media (max-width: 680px) {
    width: 100%;
  }
}
.card-img {
  overflow: hidden;
  flex-shrink: 0;
  width: 100%;
  height: 200px;
  border-top-right-radius: 4px;
  border-top-left-radius: 4px;
  img {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
.card-container {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  padding: 16px;
}
.card-title {
  font-weight: 600;
  font-size: 20px;
  line-height: 25px;
  margin-bottom: 16px;
  color: #3f3f3f;
}
.card-description {
  margin-bottom: 32px;
  font-size: 16px;
  line-height: 20px;
  color: #3f3f3f;
}
.card-price {
  margin-top: auto;
  padding-bottom: 8px;
  font-weight: 600;
  font-size: 24px;
  line-height: 30px;
  color: #3f3f3f;
}
</style>
