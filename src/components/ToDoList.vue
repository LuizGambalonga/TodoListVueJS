<template>
    <div>
          <div class="fundo">
            <h1> Crie uma lista de Tarefas que você deseja efetuar em 2022</h1>
            <input v-model.trim="task" placeholder="Digite a Tarefa">
            <button  @click="addTask" type="button" > Adicionar</button>
            <button  @click="removerList" type="button"> Remover</button>
            <ul>
               <h3>Confira sua lista logo abaixo ;) :</h3>
               <li v-for="task in tasks" :key="task">{{task}}</li>
            </ul>
        </div>
        
    </div>
</template>

<script>
    export default{
        name: "ToDoList",
        data(){
            
            return {
                task: "",
                tasks: [],
                listaVazia: "Por enquanto sua lista de Tarefas esta vazia =x",
                listaComItem: "Confira sua lista de Tarefas",
                mostraMensagem: true
            }
        },
        methods: {
            addTask(){ 
                //Valida se o campo esta vazio e da uma mensagem para o usuario adicionar um nome a tarefa.
                if(this.task ==""){
                    alert("Erro: Adicione um nome para sua tarefa!")
                   return
                }
                if(this.tasks.indexOf(this.task) ===-1) {
                   this.tasks.push(this.task)
                }else{
                      alert("Erro: Esta tarefa já foi Adicionada") 
                }
                this.task =""
            },
            removerList(){
                if(this.task.lenght <=1){
                     alert("Erro: Não há tarefas para remover")
                }else{
                    this.tasks.pop(this.task)
                }
              this.task =""
            }
        }
    }
</script>
<style>
    *{
       color: #2c3e50; 
       margin: 0;
       padding: 0;  
    }
    .fundo{
        background-color: gray;
        width: 75%;
        margin-left: auto;
        margin-right: auto;
        height: auto;
        border-radius: 5px;

    }
    h1{
        margin-bottom: 2rem;
        padding-top: 4rem;
    }
    h3{
        text-transform: uppercase;
        color: #f0e6e0;
    }
    button{
        margin: 2rem 0 2rem 1rem;
    }
    ul{
        list-style: none;
        padding-bottom: 2rem;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        border-radius: 2px;
        margin: 0 1rem 2rem 1rem;
        padding-bottom: 2rem;
        height: auto;
        width: 100%;
    }
    li{
      padding: 0.8rem;
      width: 20%;
      text-transform: uppercase;
      font-size: 1.1rem;
      color: white;
      position: relative;
      right: 60px;
      top: 20px;
      text-align: left;
    }
    input{
        height: 25px;
        border: none;
        position: relative;
        right: 20%;
        width: 300px;
        border-radius: 5px;
        outline-width: 0;
        height: 40px;
        font-size: 17px;
        margin-left: 20px;
        padding-left: 1rem;
    }
    button{
        height: 25px;
        border: none;
        position: relative;
        right: 20%;
        width: 100px;
        border-radius: 5px;
        outline-width: 0;
        height: 40px;
        font-size: 17px;
        margin-left: 20px;
    }
    button:hover{
        background-color: #b4b1e94d;
        color: white;
        transition: .5s;
    }
    input::placeholder{
        text-align:center;
        font-size: 18px;
    }
    .asteristico{
        font-size: 20px;
    }
</style>