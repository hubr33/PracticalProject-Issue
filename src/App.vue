<template>
  <div class="issue">
    <h2>Formularz zgłoszeniowy</h2>
    <main>
      <form @submit.prevent="sendIssue">
        <label for="title">Tytuł zgłoszenia</label>
        <input
          type="text"
          placeholder="Wpisz tytuł zgłoszenia..."
          v-model="issueTitle"
        />
        <label for="name">Imię</label>
        <input
          type="text"
          placeholder="Wpisz swoje imię..."
          v-model="issueName"
        />
        <label for="surname">Nazwisko</label>
        <input
          type="text"
          placeholder="Wpisz swoje nazwisko..."
          v-model="issueSurname"
        />
        <label for="issueDate">Data wystąpienia problemu</label>
        <input type="date" v-model="issueDate" />
        <label for="issueDescription">Opis problemu</label>
        <textarea
          name="problem"
          id="problem"
          cols="30"
          rows="10"
          v-model="issueDescription"
        ></textarea>
        <button class="sendIssue">Wyślij zgłoszenie</button>
      </form>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      issueTitle: "",
      issueName: "",
      issueSurname: "",
      issueDate: "",
      issueDescription: "",
    };
  },
  methods: {
    sendIssue() {
      const allInputs = document.querySelectorAll(".issue form input");
      const textArea = document.querySelector(".issue form textarea");
      if (
        this.issueTitle !== "" &&
        this.issueName !== "" &&
        this.issueSurname !== "" &&
        this.issueDate !== "" &&
        this.issueDescription !== ""
      ) {
        (this.issueTitle = ""),
          (this.issueName = ""),
          (this.issueSurname = ""),
          (this.issueDate = ""),
          (this.issueDescription = "");
        textArea.classList.remove("active");
        allInputs.forEach((input) => {
          input.classList.remove("active");
        });
      } else {
        if (textArea.value === "") {
          textArea.classList.add("active");
        } else {
          textArea.classList.remove("active");
        }
        allInputs.forEach((input) => {
          if (input.value === "") {
            input.classList.add("active");
          } else {
            input.classList.remove("active");
          }
        });
      }
    },
  },
};
</script>

<style scoped>
@import "./styles/style.css";
</style>
