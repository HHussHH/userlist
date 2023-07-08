<script>
export default {
  data() {
    return {
      userList: [
        { name: "name1", value: "value1" },
        { name: "name2", value: "value2" },
        { name: "name3", value: "value3" },
        { name: "name4", value: "value4" },
        { name: "name5", value: "value5" },
        { name: "name6", value: "value6" },
        { name: "name7", value: "value7" },
        { name: "name8", value: "value8" },
        { name: "name9", value: "value9" },
        { name: "name10", value: "value10" },
        { name: "name11", value: "value11" },
        { name: "name12", value: "value12" },
        { name: "name13", value: "value13" },
        { name: "name14", value: "value14" },
        { name: "name15", value: "value15" },
        { name: "name16", value: "value16" },
        { name: "name17", value: "value17" },
        { name: "name18", value: "value18" },
        { name: "name19", value: "value19" },
        { name: "name20", value: "value20" },
        { name: "name21", value: "value21" },
        { name: "name22", value: "value22" },
        { name: "name23", value: "value23" },
        { name: "name24", value: "value24" },
        { name: "name25", value: "value25" },
        { name: "name26", value: "value26" },
        { name: "name27", value: "value27" },
        { name: "name28", value: "value28" },
        { name: "name29", value: "value29" },
        { name: "name30", value: "value30" },
      ],
      isOpenModalWin: false,
      selectedUser: {
        name: "",
        value: "",
      },
    };
  },

  methods: {
    toggleOpenModalWin() {
      this.isOpenModalWin = !this.isOpenModalWin;
    },
    selectUser(name, value) {
      this.selectedUser.name = name;
      this.selectedUser.value = value;
      this.isOpenModalWin = true;
    },
    changeUserData(name) {
      const userIndx = this.userList.findIndex((user) => user.name === name);
      this.userList[userIndx].value = this.selectedUser.value;
      this.isOpenModalWin = false;
    },
  },
};
</script>

<template>
  <div class="userList">
    <div class="container">
      <h1 class="userList__title">Список пользователей:</h1>
      <ul class="userList__list">
        <li
          class="userList__card"
          v-for="user in userList"
          :key="user.name"
          @click="selectUser(user.name, user.value)"
        >
          <div class="userList__name">
            {{ user.name }}
          </div>
          <div class="userList__value">{{ user.value }}</div>
        </li>
      </ul>
    </div>
  </div>

  <div class="modalWindow" v-show="isOpenModalWin" @click="toggleOpenModalWin">
    <div class="modalWindow__content" @click.stop>
      <div class="modalWindow__card">
        <div class="modalWindow__closeButton" @click="toggleOpenModalWin">
          &#10006;
        </div>
        <h2 class="modalWindow__title">
          Внесение правок в информацию о пользователе.
        </h2>
        <form
          @submit.prevent="changeUserData(selectedUser.name)"
          class="modalWindow__form"
        >
          <div class="modalWindow__name">
            <p>Имя пользователя:</p>
            {{ selectedUser.name }}
          </div>
          <div class="modalWindow__value">
            <p>Данные о пользователе</p>
            <input
              class="modalWindow__inputField"
              type="text"
              v-model="selectedUser.value"
            />
          </div>
          <button
            @click.prevent="changeUserData(selectedUser.name)"
            class="modalWindow__button"
          >
            Обновить данные
          </button>
        </form>
      </div>
    </div>
  </div>
</template>
<style scoped lang="scss">
.container {
  width: 1440px;
  margin: 0 auto;
  @media (min-width: 2560px) {
    width: 2000px;
  }
  @media (max-width: 1024px) {
    width: 760px;
  }
  @media (max-width: 425px) {
    width: 400px;
  }
  @media (max-width: 320px) {
    width: 300px;
  }
}
.userList {
  margin-top: 50px;
  &__title {
    font-size: 36px;
    width: max-content;
    margin: 0 auto;
    margin-bottom: 50px;
    @media (max-width: 425px) {
      font-size: 26px;
    }
  }
  &__list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 30px;
  }
  &__card {
    border: 1px solid gray;
    width: 100px;
    align-self: flex-start;
    min-height: 100px;

    border-radius: 20px;

    cursor: pointer;

    &:hover {
      background-color: rgb(246, 243, 233);
    }
  }
  &__name {
    font-weight: 600;
    font-size: 18px;
    padding-top: 15px;
    text-align: center;
  }
  &__value {
    padding: 3px;
    width: 100%;
    word-wrap: break-word;
    word-break: break-word;
    font-weight: 500;
    font-size: 16px;
    padding-top: 5px;
  }
}

.modalWindow {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(117, 113, 113, 0.573);

  &__content {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  &__card {
    background-color: rgb(255, 255, 255);
    width: 500px;
    height: 300px;
    padding: 15px;
    border-radius: 20px;
    @media (min-width: 2560px) {
      width: 700px;
      height: 400px;
    }
    @media (max-width: 425px) {
      width: 300px;
      height: 300px;
    }
  }
  &__closeButton {
    cursor: pointer;
    margin-bottom: 10px;
    @media (min-width: 2560px) {
      font-size: 24px;
    }
    @media (max-width: 425px) {
      font-size: 14px;
    }
  }
  &__title {
    font-size: 24px;
    text-align: center;
    @media (min-width: 2560px) {
      font-size: 36px;
    }
    @media (max-width: 425px) {
      font-size: 16px;
    }
  }
  &__form {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 25px;
  }
  &__name {
    display: flex;
    gap: 5px;
    @media (min-width: 2560px) {
      font-size: 20px;
    }
  }
  &__value {
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 10px;
    align-items: center;
    @media (min-width: 2560px) {
      font-size: 20px;
    }
  }
  &__inputField {
    padding: 5px;
    font-size: 16px;
    border-radius: 20px;
    border: 2px solid black;
    @media (min-width: 2560px) {
      font-size: 20px;
    }
  }
  &__button {
    background-color: rgb(46, 183, 183);
    padding: 10px 15px;
    border: none;
    border-radius: 20px;
    font-size: 14px;
    color: white;
    font-weight: 600;
    cursor: pointer;
    @media (min-width: 2560px) {
      padding: 15px 20px;
      font-size: 16px;
    }
  }
}
</style>
