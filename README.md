// Lista de tarefas
let tarefas = [];

// Função anônima para adicionar tarefa
let adicionarTarefa = function(tarefa) {
    tarefas.push({ descricao: tarefa, concluida: false });
    console.log(`Tarefa adicionada: "${tarefa}"`);
};

// Arrow function para listar tarefas
let listarTarefas = () => {
    console.log("Lista de Tarefas:");
    tarefas.forEach((tarefa, index) => {
        let status = tarefa.concluida ? "[✔️]" : "[ ]";
        console.log(`${index}: ${status} ${tarefa.descricao}`);
    });
};

// Função que usa callback para manipular a lista
function processarTarefa(callback) {
    callback();
}

// Funções de callback para remover, atualizar e concluir tarefas
let removerTarefa = () => {
    let index = parseInt(prompt("Digite o índice da tarefa que deseja remover:"));
    if (!isNaN(index) && tarefas[index]) {
        console.log(`Tarefa removida: "${tarefas[index].descricao}"`);
        tarefas.splice(index, 1);
    } else {
        console.log("Índice inválido.");
    }
};

let atualizarTarefa = () => {
    let index = parseInt(prompt("Digite o índice da tarefa que deseja atualizar:"));
    if (!isNaN(index) && tarefas[index]) {
        let novaDescricao = prompt("Digite a nova descrição da tarefa:");
        console.log(`Tarefa "${tarefas[index].descricao}" atualizada para "${novaDescricao}"`);
        tarefas[index].descricao = novaDescricao;
    } else {
        console.log("Índice inválido.");
    }
};

let concluirTarefa = () => {
    let index = parseInt(prompt("Digite o índice da tarefa que deseja marcar como concluída:"));
    if (!isNaN(index) && tarefas[index]) {
        tarefas[index].concluida = true;
        console.log(`Tarefa "${tarefas[index].descricao}" marcada como concluída.`);
    } else {
        console.log("Índice inválido.");
    }
};

// Loop de interação com o usuário
function menu() {
    let opcao;
    do {
        opcao = prompt(
            "Escolha uma opção:\n1 - Adicionar Tarefa\n2 - Listar Tarefas\n3 - Remover Tarefa\n4 - Atualizar Tarefa\n5 - Concluir Tarefa\n0 - Sair"
        );

        switch (opcao) {
            case "1":
                let tarefa = prompt("Digite a descrição da nova tarefa:");
                adicionarTarefa(tarefa);
                break;
            case "2":
                listarTarefas();
                break;
            case "3":
                processarTarefa(removerTarefa);
                break;
            case "4":
                processarTarefa(atualizarTarefa);
                break;
            case "5":
                processarTarefa(concluirTarefa);
                break;
            case "0":
                console.log("Saindo do gerenciador de tarefas.");
                break;
            default:
                console.log("Opção inválida.");
        }
    } while (opcao !== "0");
}

// Iniciar o menu
menu();
