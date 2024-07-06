## <span style="color:#3E347B">Course Progress</span>

### Utilidade
É a barra de progresso. Pode-se controlar a porcentagem, que controla a exibição e o número na parte de baixo.

### Implementação
Esse componente tem 2 parametros principais. Sendo `.texto` que controla o texto que é exibido na borda da barra, e `.progress`, que controla  a barra de progresso. Esse parâmetros são passados através do props.

A implementação é bem simples, abaixo uma amostra do codigo js e css:

<table>
<tr>
<th>JS</th>
<th>CSS</th>
</tr>
<tr>
<td>
<pre>
<div>

export default function CourseProgress(props) {
    return (
`       <div className="course-progress"> `
        `<span className='label'>{props.texto} </span> `
        `<div className="progress-border"> `
            <div className="progress-bar" style={{ width:` ${props.progress}%' }}> `
        `       </div> ` 
    `<p className="progress-percent">{props.progress}% </p> `
        `</div>` 
    )
}
</pre>
</td>
<td>

```json
.progress-bar{
    background-color: #F2953F;
    height: 0.5em;
}
.progress-border{
    width: 100%;
    border-color: #454545;
    border-style: solid;
}
```
</td>
</tr>
</table>

As partes mais importantes a se observar são as classes `progress-bar`e `progress-border`. Veja que a `progress-bar`está dentro da `progress-border`, isso porque é um retângulo, com tamanho controlado pela `progress-border`. A barra de progresso atualiza conforme o tanto que está preenchido do retângulo, recebendo como parametro lá no JS, a porcentagem que ele deve percorrer. 

Um detalhe importante, é que a barra de progresso atualmente ocupa 100% do comprimento da div que ela está inserida. Isso foi feito pra funcionar melhor com as ferramentas do bootstrap.
### Exemplo

![alt](/Front/img/CourseProgress.png "imagem")
#

## <span style="color:#3E347B">File Uploader</span>

### Utilidade
Esse componente é utilizado para fazer upload de uma imagem, além de permitir a visualização da mesma na tela, dando uma prévia de como vai ficar na exibição.

### Implementação
A implementação é um pouco complicada, já que esse uploader precisa dos hooks do React, além de uma configuração específica no css pra exibir da maneira correta.

Basicamente, é um botão camuflado com uma imagem, que quando clicado faz o handling do upload e exibição da imagem:

```
export const FileUploader = ({handleFile}) => {  // Create a reference to the hidden file input element
  const hiddenFileInput = useRef(null);
  const handleClick = event => {
    hiddenFileInput.current.click();
  };  
  const [file, setFile] =useState(SaveCloud);
    

  const handleChange = event => {
    const fileUploaded = event.target.files[0];
    handleFile(fileUploaded);
    setFile(URL.createObjectURL(fileUploaded)); 
    
  };

return (
    <>
      <button className="button-upload" onClick={handleClick}>
        <img className="save-cloud" src={file}/>
      </button>
      <input
        type="file"
        onChange={handleChange}
        ref={hiddenFileInput}
        style={{display: 'none'}} // Make the file input element invisible
      />
    </>
  );
};
export default FileUploader;
```
Dentro da tag button tem uma imagem, que serve como botão. Ao ser clicado, é chamada a função `handleClick`, que lida com a seleção da imagem. Após isso, a função `handleChange` muda a imagem do botão para a imagem que foi feito o upload.

Observe que dentro da tag input, foi definido o display para `none`, isso porque o upload padrão de imagens do html é acompanhado de um botão escrito "browse", que acompanharia a imagem padrão, por isso foi removido. Então basicamente, temos um uploader customizavel.


### Exemplo

Antes de selecionar a imagem (O componente é essa nuvem dentro do quadrado)

![alt](/Front/img/FileUploader1.png "imagem")

Após selecionar a imagem

![alt](/Front/img/FileUploader2.png "imagem")

# 

## <span style="color:#3E347B">Footer</span>

### Utilidade

Esse component é responsável pelo footer da página. Atualmente ele está um pouco desalinhado, seria bom um refactor dele.

### Implementação

Basicamente, foi utilizado as ferramentas do bootstrap para footer, e editado conforme as necessidades do nosso design, adicionando algumas classes para estilizar corretamente

### Exemplo

![alt](/Front/img/Footer.png "imagem")

#

## <span style="color:#3E347B">Input</span>

### Utilidade
Esse componente é utilizado para gerar campos de form para serem preenchidos, tomando como parametros  `name` e `value`. O `name` define o nome que vai aparecer acima do campo a ser preenchido, e o `value` define o seu valor, sendo muito útil para os hooks do react e integração com o back.


### Implementação
    export default function Input(props){
    return (

    <div className="mb-4">
        <label htmlFor={props.name} className="form-label">{props.name}</label>
        <input
            type={props.type || "text"}
            className="form-input"
            value={props.value}
            onChange={(e) => props.setValue(e.target.value)}
        />
        {props.children}
    </div>
        
    );
    }

A implementação é bem simples. A tag `<input>` recebe os parametros do tipo e do valor, e os seta para o campo.

### Exemplo

![alt](/Front/img/Input.png "imagem")

O titulo dos campos é o parâmetro `name`, e o que é guardado como "variável" , é o que é preenchido dentro do campo, o `value`.

 