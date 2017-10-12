ALGORITMO DE CIFRADO DE CESAR
__________________________


Este programa te permite encriptar mensajes segun el algoritmo de cifrado César.

Elegir una opcion  para elegir si se desea:

Con este programa se puede:
* Cifrar una palabra
	-Se puede combinar letras mayusculas con minusculas.
        -Acepta espacios.
* Descifrar una palabra
	-Se puede combinar letras mayusculas con minusculas.
        -Acepta espacios.

 
La palabra ingresada en la caja de texto no  debe :
1. Ser de longitud igual a 0 
2. Contener algun número
3. Poseer operadores lógicos

Presentamos los diagramas de flujo:
![recursos](assets/docs/general.jpg)
![recursos](assets/docs/cipher.jpg)
![recursos](assets/docs/decipher.jpg)
 
 
Procedemos a explicar el pseudocódigo
```[javascript]

function cipher() {
  word=prompt('Ingrese la palabra a cifrar');//Se pide que ingrese la palabra a cifrar.
  var output=""; //Se declara la variable donde se acumulara la salida luego de ser cifrada
  if (word.length>0){ //Se condiciona en el caso que la longitud de la palabra ingresada sea mayor a 0
    for (i=0;i<word.length;i++){
    keyCode=word.charCodeAt(i);//Obtenemos el codigo ascii de cada caracter de la palabra ingresada 
     if ((keyCode != 32) && (keyCode < 65) || (keyCode > 90) && (keyCode < 97) || (keyCode > 122) ){ //Restringimos en el caso que la palabra posea números o caracteres invalidos
     console.log('Por favor ingrese una palabra válida');
     break;
     }
     else
     { //En el caso que la palabra solo posea letras procedera a hacer el cifrado Cesar
      for (var j=0; j<word.length;j++){
  		output += String.fromCharCode((word.charCodeAt(j)-65+33)%26+65);
  		}
      return output;    
      
     }
    }
    
  }
  else
  { //En el caso que no ingrese nada nos enviara un mensaje en la consola
    console.log('Ha ingresado un texto vacio');
  }
  
}


function decipher() {
  word=prompt('Ingrese la palabra a descifrar'); //Se pide que ingrese la palabra a descifrar.
  var output="";//Se declara la variable donde se acumulara la salida luego de ser cifrada
  if (word.length>0){ //Se condiciona en el caso que la longitud de la palabra ingresada sea mayor a 0
    for (i=0;i<word.length;i++){
    keyCode=word.charCodeAt(i); //Obtenemos el codigo ascii de cada caracter de la palabra ingresada 
     if ((keyCode != 32) && (keyCode < 65) || (keyCode > 90) && (keyCode < 97) || (keyCode > 122) ){//Restringimos en el caso que la palabra posea números o caracteres invalidos
     console.log('Por favor ingrese una palabra válida');
     break;
     }
     else
     {//En el caso que la palabra solo posea letras procedera a hacer el descifrado Cesar
      for (var j=0; i<word.length;j++){
		  var asciiCode = ((word.charCodeAt(j)-65+26+26-33) % 26)+65;
		  output += String.fromCharCode(asciiCode);
		 }
      return output;   //Devuelve la palabra ya descifrada
     }
    }
  }
  else
  { //En el caso que no ingrese nada nos enviara un mensaje en la consola
    console.log('Ha ingresado un texto vacio');
  }
}


//Presentamos una pantalla con las opciones a elegir según lo que desea realizar
selectOption=parseInt(prompt('Ingrese la acción que desea realizar \n 1.Cifrar un texto \n 2.Descifrar un texto '));

switch (selectOption) {//Empleamos el switch case para restringir a solo 2 opciones lo que el usuario puede marcar
   
    case 1:
        console.log(cipher());//En el caso que marque 1 se invocará a la función cipher.
        break;
    case 2:
        console.log(decipher());//En el caso que marque 2 se invocará a la función decipher.
        break;
   default:
        alert('Debe ingresar opciones entre 1 o 2 ')
        

}


