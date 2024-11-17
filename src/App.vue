<template>
  <div id="app">
    <!-- Cabeçalho -->
    <header class="header">
      <h1>Minha Lista de Tarefas</h1>
      <p>Organize suas tarefas de forma prática e eficiente.</p>
    </header>

    <!-- Corpo principal -->
    <main class="main">
      <section class="task-input">
        <input type="text" v-model="newTask" placeholder="Digite sua tarefa..." />
        <button @click="addTask">Adicionar</button>
      </section>
      <section class="task-list">
        <ul>
          <li v-for="(task, index) in tasks" :key="index">
            <span>{{ task }}</span>
            <button @click="removeTask(index)">Remover</button>
          </li>
        </ul>
      </section>
    </main>

    <!-- Rodapé -->
    <footer class="footer">
      <p>&copy; 2024 Lista de Tarefas - Desenvolvido com Vue.js</p>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: "", // Armazena o texto da nova tarefa
      tasks: [] // Armazena as tarefas
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== "") {
        this.tasks.push(this.newTask);
        this.newTask = ""; // Limpa o campo de entrada
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1); // Remove a tarefa pelo índice
    }
  }
};
</script>

<style scoped>
/* Insira o CSS adaptado aqui */
body {
  font-family: Arial, Helvetica, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f4f4f4;
  color: #333;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.header {
  background-color: #007bff;
  color: white;
  text-align: center;
  padding: 20px 10px;
}

.header h1 {
  margin: 0;
  font-size: 2.5em;
}

.header p {
  margin: 5px 0 0;
  font-size: 1.2em;
}

.main {
  flex: 1;
  padding: 20px;
}

.task-input {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.task-input input {
  width: 60%;
  padding: 10px;
  font-size: 1em;
  border: 1px solid #ccc;
  border-radius: 5px 0 0 5px;
}

.task-input button {
  padding: 10px 20px;
  font-size: 1em;
  border: none;
  background-color: #007bff;
  color: white;
  cursor: pointer;
  border-radius: 0 5px 5px 0;
  transition: background-color 0.3s;
}

.task-input button:hover {
  background-color: #0056b3;
}

.task-list {
  max-width: 600px;
  margin: 0 auto;
  background: #fff;
  padding: 15px;
  border-radius: 10px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.task-list ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.task-list li {
  display: flex;
  justify-content: space-between;
  padding: 10px;
  margin: 5px 0;
  background: #f9f9f9;
  border: 1px solid #ddd;
  border-radius: 5px;
}

.task-list li span {
  flex: 1;
}

.task-list li button {
  border: none;
  background: #ff4d4d;
  color: white;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.task-list li button:hover {
  background: #cc0000;
}

.footer {
  background-color: #333;
  color: white;
  text-align: center;
  padding: 10px;
  font-size: 0.9em;
}
</style>
