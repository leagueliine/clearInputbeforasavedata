import React, { useState } from "react";

function App() {

  const [user, setUser] = useState({
    name: '',
    email: '',
    password: ''
  });

  const [status, setStatus] = useState({
    type: '',
    mensagem: ''
  });

  //Receber os dados do formulário
  const valueInput = e => setUser({ ...user, [e.target.name]: e.target.value });

  //Enviar os dados para o back-end
  const addUser = async e => {
    e.preventDefault();

    const saveDataForm = true;

    if (saveDataForm) {
      setStatus({
        type: 'success',
        mensagem: "Usuário cadastrado com sucesso!"
      });
      setUser({
        name: '',
        email: '',
        password: ''
      });
    } else {
      setStatus({
        type: 'error',
        mensagem: "Erro: Usuário não cadastrado com sucesso!"
      });
    }


  }

  return (
    <div>
      <h1>Cadastrar Usuário</h1>

      {status.type === 'success' ? <p style={{ color: "green" }}>{status.mensagem}</p> : ""}
      {status.type === 'error' ? <p style={{ color: "#ff0000" }}>{status.mensagem}</p> : ""}

      <form onSubmit={addUser}>
        <label>Nome*: </label>
        <input type="text" name="name" placeholder="Nome completo do usuário" onChange={valueInput} value={user.name} /><br /><br />

        <label>E-mail*: </label>
        <input type="email" name="email" placeholder="Melhor e-mail do usuário" onChange={valueInput}  value={user.email} /><br /><br />

        <label>Senha*: </label>
        <input type="password" name="password" placeholder="Senha para acessar o sistema" autoComplete="on" onChange={valueInput} value={user.password} /><br /><br />

        * Campo obrigatório<br /><br />

        <button type="submit">Cadastrar</button>
      </form>
    </div>
  );
}

export default App;



//

my code
app.js//
import { handleSubmit, register } from 'react-hook-form'
import { FormRegister } from './form-teste'

const { register, handleSubmit } = useForm();
const {nome, setNome} = useState('');


const App = () => {
    return(

        <>
        <FormRegister value={nome} onChange={(e) => setNome = e.target.value} />
        </>

    )
}
end of app.js//

//form.js

import { useForm } from 'react-hook-form'
import { InputMask } from 'react-input-mask' 
import { useState } from 'react'


const FormRegister = ( {value, onChange} ) => {

        const onSubmit = (e) => {
            alert(JSON.stringify(e))
        };
        

    return(
        <>
        <form onSubmit={handleSubmit(onSubmit)}>

            <InputMask
            mask='999.999.999-99'
            type={props.type}
            placeholder={props.placeholder}
            value={value}
            onChange={onChange} />

            <input type='submit' />
            
        </form>
        </>
    )
}

end of form.js//


