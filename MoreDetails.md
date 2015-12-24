A production could contains other production definitions inside it, when some part of the code makes use of this, its definitions are pasted too.

#### These definitions: ####
```js

p1
{
p2{v2}
}

result
{
p1
}
```
#### Generates this result: ####
```js

p1
{
p2{v2}
}
result
{
v2{v2}
}
```


#### Example 1: complete program with byte, nibble and vector definition, addition and multiplication : ####
```

programa
{

sistema:macros de sintaxis
{
<funcion>{}
<procedimiento>{%}
<metodo>{%}
<clase>{nuevo}
<cierra clase>{termina_de_crear_la_clase_}
}

sistema:ayudantes1
{
[te{[t}mp]{emp]}
[re{[r}m]{em]}
[nada]{}
<*>{%}
<**{<*}
}

<clase> del
{
<metodo> del=>( %del::head %del::tail )
{
head=>%del::head %del::tail tail=>%del::head %del::tail
{
head2=>%del::head %del::tail tail2=>%del::head %del::tail
}
}

head=>%del::head %del::tail {%del::head}
tail=>%del::head %del::tail {%del::tail}
head2=>%del::head %del::tail {h}
tail2=>%del::head %del::tail {ead=>%del::head %del::tail tail=>%del::head %del::tail}
}
<cierra clase> del
{
%del=>({%del->(}head=>{head->}tail=>{tail->}ead=>{ead->}head2=>{head2->}tail2=>{tail2->}
}

<clase> math
{
<metodo> math.incr
{
<**>resultado{%incr::valor.incr}
}
<metodo> math.decr
{
<**>resultado{%decr::valor.decr}
}

<funcion> 000+ {<**>resultado{0} <**>acarreo{0}}
<funcion> 001+ {<**>resultado{1} <**>acarreo{0}}
<funcion> 010+ {<**>resultado{1} <**>acarreo{0}}
<funcion> 011+ {<**>resultado{0} <**>acarreo{1}}

<funcion> 100+ {<**>resultado{1} <**>acarreo{0}}
<funcion> 101+ {<**>resultado{0} <**>acarreo{1}}
<funcion> 110+ {<**>resultado{0} <**>acarreo{1}}
<funcion> 111+ {<**>resultado{1} <**>acarreo{1}}

15.decr{14}14.decr{13}13.decr{12}12.decr{11}11.decr{10}10.decr{9}9.decr{8}8.decr{7}7.decr{6}6.decr{5}5.decr{4}4.decr{3}3.decr{2}2.decr{1}1.decr{0}0.decr{15}
0.incr{1}1.incr{2}2.incr{3}3.incr{4}4.incr{5}5.incr{6}6.incr{7}7.incr{8}8.incr{9}9.incr{10}10.incr{11}11.incr{12}12.incr{13}13.incr{14}14.incr{15}15.incr{0}
0.esCero{true}1.esCero{false}2.esCero{false}3.esCero{false}4.esCero{false}5.esCero{false}6.esCero{false}7.esCero{false}8.esCero{false}9.esCero{false}10.esCero{false}11.esCero{false}12.esCero{false}13.esCero{false}14.esCero{false}15.esCero{false}

true.not {false}
false.not {true}

<*>del::head{%resul} <*>del::tail{tado} [temp]{nuevo del}
}

sistema:ayudantes2
{
sistema:abro_corchete{[}

#0 {<**>vector::valor{0} agrega_digito}
#1 {<**>vector::valor{1} agrega_digito}
agrega_digito {<**>llama_add {%vector_actual.agregar}<*>llama_add}
}

<clase> vector
{
[temp]defino_dels
{
<**>del::head{%vector:} <**>del::tail{:valor}	[temp]{<**>nuevo del}
<**>del::head{%vector:} <**>del::tail{:posicion}[temp]{<**>nuevo del}
}

[temp]borro_parametros
{
[temp]borro_valor{<*>del->(%vector::valor)}
[temp]borro_posicion{<*>del->(%vector::posicion)}
}

<metodo> vector::nombre.agregar
{
<***>vector::posicion {%vector::nombre.indice.getValor}
[temp]cambio_el_valor{<*>vector::nombre.cambio}
<*>vector::nombre.indice.inc
}

<metodo> vector::nombre.cambio
{
<*>vector::nombre <*>sistema:abro_corchete <*>vector::posicion ]{%vector::valor}
}

[temp]creo_nibble
{
<**>nibble::nombre {<*>vector::nombre.indice}
nuevo nibble
}
[temp]pongo_en_cero
{
<**>nibble::numero {0}
<**>vector::temp{<*>vector::nombre.indice.setValor}<*>vector::temp
}

<metodo> vector::nombre%[{<*>vector::nombre[}
}

<clase> nibble
{
[temp]defino_dels
{
<**>del::head{<*>nibble::nombre} <**>del::tail{.getValor} 	[temp]{<**>nuevo del}
<**>del::head{<*>nibble::nombre} <**>del::tail{.dec} 			[temp]{<**>nuevo del}
<**>del::head{<*>nibble::nombre} <**>del::tail{.inc} 			[temp]{<**>nuevo del}
<**>del::head{<*>nibble::nombre} <**>del::tail{.esCero} 		[temp]{<**>nuevo del}
<**>del::head{%nibble:} 			<**>del::tail{:numero} 		[temp]{<**>nuevo del}
}

[temp]borro_parametros
{
<*>del->(%nibble::numero)
}

<metodo> nibble::nombre.setValor
{
[temp]borra_metodos
{
[temp]{<*>del=>(%nibble::nombre.getValor)}
[temp]{<*>del=>(%nibble::nombre.dec)}
[temp]{<*>del=>(%nibble::nombre.inc)}
[temp]{<*>del=>(%nibble::nombre.esCero)}
}

<metodo> nibble::nombre.dec
{
<****>decr::valor {<*>nibble::nombre.getValor}
[temp]{<***>math.decr}
[temp]borra_getValor{<**>del=>(%nibble::nombre.getValor)}
<*>nibble::nombre.getValor {<***>resultado}
[temp]borra_resultado{<***>del->(%resultado)}
}
[temp]borra_getValor {<*>del=>(%nibble::nombre.getValor)}

<metodo> nibble::nombre.inc
{
<****>incr::valor {<*>nibble::nombre.getValor}
[temp]{<***>math.incr}
[temp]borra_getValor{<**>del=>(%nibble::nombre.getValor)}
<*>nibble::nombre.getValor {<***>resultado}
[temp]borra_resultado{<***>del->(%resultado)}
}
[temp]borra_getValor {<*>del=>(%nibble::nombre.getValor)}

<metodo> nibble::nombre.esCero
{
<*>nibble::nombre.getValor.esCero
}

<metodo> nibble::nombre.getValor
{
%nibble::numero
}
}
}

<clase> while
{
<metodo> while::nombre true
{
[rem]ejecuta_cuerpo{<*>while::nombre.cuerpo}
[rem]llama_a_ejecutar{%while::nombre.ejecutar}
}

<metodo> while::nombre.ejecutar
{
[rem]ejecuta_guarda{%while::nombre.guarda}
<***>while.guarda{%while::nombre.valorGuarda}
<***>while::temp{<*>while::nombre->%while.guarda}<**>while::temp
}

<metodo> while::nombre->{<*>while::nombre}
}

<procedimiento> sumar
{
[temp]defino_dels
{
<**>del::head{%suma:} <**>del::tail{:numero1} [temp]{<**>nuevo del}
<**>del::head{%suma:} <**>del::tail{:numero2} [temp]{<**>nuevo del}
}

<**>while::nombre {<**>suma.while}
[rem]creo_while{<**>nuevo while}

<**>suma.while.cuerpo
{
<***>valor1{<*>suma::numero1%[%suma.contador.getValor]}
<***>valor2{<*>suma::numero2%[%suma.contador.getValor]}

[rem]sumo_valores
{
<***>sumando {<**>ultimo_acarreo %valor1 %valor2+} <**>sumando
}

[rem]asigno_resultado
{
<***>vector::posicion {<**>suma.contador.getValor}
<***>vector::valor {<**>resultado}
<*>suma::numero1.cambio
}

<***>ultimo_acarreo {<**>acarreo}

[rem]decremento_contador{<**>suma.contador.dec}
}

<*>suma.while.guarda
{
<**>guarda_temp1	{<**>suma.contador.getValor.incr.esCero.not}
<**>guarda_temp2	{<*>guarda_temp1}<**>guarda_temp3{<*>guarda_temp2}<**>guarda_temp4{<*>guarda_temp3}
<**>suma.while.valorGuarda {<*>guarda_temp4}
}

[rem]creo_contador 	{<**>nibble::nombre {%suma.contador} <**>nuevo nibble}
[rem]seteo_contador 	{<**>nibble::numero {%suma::digitos} %suma.contador.setValor}

<**>ultimo_acarreo {0}

[rem]ejecuta {%suma.while.ejecutar}

[temp]borro_parametros
{
[temp]borro_numero1{<*>del->(%suma::numero1)}
[temp]borro_numero2{<*>del->(%suma::numero2)}
}

}



<clase> byte
{
[temp]defino_dels
{
<**>del::head{%byte:} <**>del::tail{:nuevo_valor} 			[temp]{<**>nuevo del}
<**>del::head{%byte:} <**>del::tail{:sumar::byte} 			[temp]{<**>nuevo del}
<**>del::head{<*>nibble::nombre} <**>del::tail{.inc} 			[temp]{<**>nuevo del}
<**>del::head{<*>nibble::nombre} <**>del::tail{.esCero} 		[temp]{<**>nuevo del}
<**>del::head{%nibble:} 			<**>del::tail{:numero} 		[temp]{<**>nuevo del}
}

[temp]borro_parametros
{
<*>del->(%byte::nuevo_valor)
<*>del->(%byte::sumar::byte)
}

[rem]creo_vector_para_valor {<**>vector::nombre {<*>byte::nombre.valor} <**>nuevo vector}

<metodo> byte::nombre.asignar
{
<***>vector_actual {<*>byte::nombre.valor}
<**>byte::nuevo_valor
}

<metodo> byte::nombre.decrementar
{
[rem]parametro_para_suma	{<***>byte::sumar::byte {<*>byteMenosUno}}
[rem]lo_sumo					{<*>byte::nombre.sumar}
}

<metodo> byte::nombre.incrementar
{
[rem]parametro_para_suma	{<***>byte::sumar::byte {<*>byteUno}}
[rem]lo_sumo					{<*>byte::nombre.sumar}
}

<metodo> byte::nombre.sumar
{
<***>suma::numero1{<*>byte::nombre.valor}
<***>suma::numero2{<*>byte::sumar::byte.valor}
<***>suma::digitos{7}
[rem]sumo{<**>sumar}
}

<metodo> byte::nombre.esCero
{
<***>resultado{false}
<***>byte::temp{byte:esCero:}
[rem]astring{<*>byte::nombre.toString}
<***>sera cero?{<*>byte::temp %comoString}
<*>seracero?
}

<metodo> byte::nombre.toString
{
[rem]concateno_bits	{<***>comoString{<*>byte::nombre.valor[7]}	<***>comoString{<*>byte::nombre.valor[6]%comoString }	<***>comoString{<*>byte::nombre.valor[5]%comoString } <***>comoString{<*>byte::nombre.valor[4]%comoString }	<***>comoString{<*>byte::nombre.valor[3]%comoString }	<***>comoString{<*>byte::nombre.valor[2]%comoString }	<***>comoString{<*>byte::nombre.valor[1]%comoString }	<***>comoString{<*>byte::nombre.valor[0]%comoString }	<***>mi_nombre{<*>byte::nombre=}}
<**>mi_nombre %comoString{}
}
}
<cierra clase> byte
{
[rem]es_cero				{byte:esCero:00000000{<**>resultado{true}}}

[rem]creo_byteMenosUno	{<*>byte::nombre{%byteMenosUno} nuevo byte }
[rem]le_asigno_un_valor	{<*>byte::nuevo_valor{<**>#1#1#1#1#1#1#1#1} %byteMenosUno.asignar}

[rem]creo_byteUno			{<*>byte::nombre{%byteUno} nuevo byte }
[rem]le_asigno_un_valor	{<*>byte::nuevo_valor{<**>#0#0#0#0#0#0#0#1} %byteUno.asignar}
}

[rem]prueba multiplicacion
{
<*> mul.while.cuerpo
{
[rem]sumo_con_b3		 		{<**>byte::sumar::byte {<*>b3} <*>b2.sumar}
[rem]decremento				{<*>b1.decrementar}
}

<*> mul.while.guarda
{
<**>guarda_temp1	{<*>b1.esCero}
<**>guarda_temp2	{<*>resultado.not}
<**>mul.while.valorGuarda {<*>guarda_temp2}
}

[rem]creo_byte1				{<*>byte::nombre{%b1} nuevo byte }
[rem]le_asigno_un_valor		{<*>byte::nuevo_valor{<**>#0#0#0#0#0#1#1#0} %b1.asignar}
[rem]creo_byte2				{<*>byte::nombre{%b2} nuevo byte }
[rem]le_asigno_un_valor		{<*>byte::nuevo_valor{<**>#0#0#0#0#0#1#0#0} %b2.asignar}
[rem]creo_byte3				{<*>byte::nombre{%b3} nuevo byte }
[rem]le_asigno_un_valor		{<*>byte::nuevo_valor{<**>#0#0#0#0#0#1#0#0} %b3.asignar}

<*>while::nombre 				{<*>mul.while}
[rem]creo_while				{<*>nuevo while}

[rem]ejecuta 					{%mul.while.ejecutar}

[rem]valor						{%b2.toString }

}

[rem]prueba_de_byte
{
[rem]creo_byte1				{<*>byte::nombre{%b1} nuevo byte }
[rem]le_asigno_un_valor		{<*>byte::nuevo_valor{<**>#0#1#1#1#0#1#1#0} %b1.asignar}

[rem]valor						{%b1.toString }
[rem]lo_decremento 			{%b1.decrementar}
[rem]valor						{%b1.toString }

[rem]creo_byte2				{<*>byte::nombre{%b2} nuevo byte }
[rem]le_asigno_un_valor		{<*>byte::nuevo_valor{<**>#1#1#0#0#0#1#0#1} %b2.asignar}
[rem]valor						{%b2.toString }
[rem]parametro_para_suma	{<*>byte::sumar::byte {<*>b2}}
[rem]lo_sumo_con_b2			{%b1.sumar}
[rem]valor						{%b1.toString }

[rem]valor						{%byteUno.toString }
[rem]nose{%byteUno.decrementar}
[rem]valor						{%byteUno.toString }

[rem]me fijo si es cero 	{%byteUno.esCero}
}


[rem]prueba de suma
{
[rem]creo_vector{<*>vector::nombre {%va1} nuevo vector}
[rem]asigno_vector{<*>vector_actual {%va1} #1#1#0#1#1}

[rem]creo_vector{<*>vector::nombre {%va2} nuevo vector}
[rem]asigno_vector{<*>vector_actual {%va2} #1#1#1#0#1}

[rem]primer numero  {%va1[0] %va1[1] %va1[2] %va1[3] %va1[4]}
[rem]segundo numero {%va2[0] %va2[1] %va2[2] %va2[3] %va2[4]}

<*>suma::numero1{<*>va1}
<*>suma::numero2{<*>va2}
<*>suma::digitos{4}
[rem]sumo{%sumar}

[rem]numeros sumados{%va1[0] %va1[1] %va1[2] %va1[3] %va1[4]}
}



[rem]prueba_de_while
{
[rem]cargo_nombre{<*>while::nombre{%w1}}
[rem]creo_while{nuevo while}
[rem]creo_guarda{%w1.guarda{<**>w1.valorGuarda{%contador.esCero.not}}}
[rem]creo_cuerpo{%w1.cuerpo{%contador.dec}}

[rem]creo_contador{<*>nibble::nombre{%contador}nuevo nibble}
[rem]seteo_contador{<*>nibble::numero{8}%contador.setValor}
%w1.ejecutar
}

[rem]prueba_de_vector
{
[rem]cargo_nombre{<*>vector::nombre{%v1}}
[rem]creo_vector{nuevo vector}

[rem]cargo_numero{<*>vector::valor{"hola"}}
[rem]seteo_el_valor{%v1.agregar}

[rem]cargo_numero{<*>vector::valor{"mundo"}}
[rem]seteo_el_valor{%v1.agregar}

[temp]pos0{%v1[0]}
[temp]pos1{%v1[1]}
}


[rem]prueba_de_nibble
{
[rem]cargo_nombre{<*>nibble::nombre{%n1}}
[rem]creo_nibble{nuevo nibble}

[rem]cargo_numero{<*>nibble::numero{5}}
[rem]seteo_el_valor{%n1.setValor}
[rem]lo_decremento{%n1.dec}

[rem]cargo_numero{<*>nibble::numero{11}}
[rem]seteo_el_valor{%n1.setValor}
[rem]lo_incremento{%n1.inc}
}

}
```