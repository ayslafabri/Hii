const botaoAdicionar = document.getElementById('add-task');
const inputTarefa = document.getElementById('task-input');
const listaTarefas = document.getElementById('task-list');

botaoAdicionar.addEventListener('click', adicionarTarefa);
inputTarefa.addEventListener('keypress', function(e) {
    if (e.key === 'Enter') adicionarTarefa();
});

function adicionarTarefa() {
    const textoTarefa = inputTarefa.value.trim();
    if (textoTarefa === '') return;

    const li = document.createElement('li');
    li.textContent = textoTarefa;

    const botaoRemover = document.createElement('button');
    botaoRemover.textContent = '❌';
    botaoRemover.onclick = () => li.remove();

    // Marcar como concluída ao clicar na tarefa
    li.addEventListener('click', () => li.classList.toggle('concluida'));

    li.appendChild(botaoRemover);
    listaTarefas.appendChild(li);
    inputTarefa.value = '';
}
