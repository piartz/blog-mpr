---
layout: default
title: "Mellorando unha shell en Linux"
date: 2025-01-03
---


# Mellorando unha shell en Linux

O primeiro paso é executar o seguinte comando: 

```bash
python -c 'import pty;pty.spawn("/bin/bash")'
```

Este comando usa Python para lanzar unha shell bash con mellores características. Ten en conta que algúns obxectivos poden requirir unha versión específica de Python. Se este é o caso, substitúe `python` por `python2` ou `python3`, segundo sexa necesario. Neste punto, a nosa shell terá un aspecto un pouco máis cómodo, pero aínda non teremos acceso á autocompletación co tabulador nin ás frechas de dirección, e o atallo **Ctrl + C** seguirá matando a shell.

### Paso 2: Configurar o terminal
Exportamos a variable de entorno `TERM` para acceder a comandos básicos de terminal, como `clear`:

```bash
export TERM=xterm
```

Isto mellorará o comportamento de certos comandos, pero aínda non completará o proceso.

### Paso 3: Configurar correctamente a terminal
Agora necesitamos pasar a shell ao fondo usando **Ctrl + Z**. No noso propio terminal executamos:

```bash
stty raw -echo; fg
```

Isto fai dúas cousas fundamentais:
1. Desactiva o "echo" do noso terminal, o que nos permite usar a autocompletación co tabulador, as frechas de dirección e **Ctrl + C** para matar procesos.
2. Trae a shell de novo ao primeiro plano (**foreground**), completando así o proceso.

Unha vez feito isto, teremos unha shell completamente funcional e lista para traballar.

# Usando rlwrap para mellorar unha shell

`rlwrap` é un programa que, en termos simples, nos dá acceso inmediato ao historial, á autocompletación co tabulador e ás frechas de dirección ao recibir unha shell. Non obstante, aínda será necesario realizar unha estabilización manual se desexamos usar **Ctrl + C** dentro da shell. 

Por defecto, `rlwrap` non está instalado en Kali Linux, polo que primeiro temos que instalalo executando:

```bash
sudo apt install rlwrap
```

### Usar `rlwrap` cun listener
Para usar `rlwrap`, debemos invocar un listener de Netcat lixeiramente modificado:

```bash
rlwrap nc -lvnp <port>
```

Ao engadir `rlwrap` antes do noso listener de Netcat, obtemos unha shell moito máis funcional. Esta técnica é especialmente útil ao traballar con shells de Windows, que son coñecidas por ser especialmente difíciles de estabilizar.

### Estabilización completa en sistemas Linux
Cando traballamos cun obxectivo Linux, é posible estabilizar completamente a shell usando o mesmo truco do paso tres da técnica anterior: 

1. Pasar a shell ao fondo co atallo **Ctrl + Z**.
2. No noso terminal, executar o seguinte comando para estabilizar e reentrar na shell:
   ```bash
   stty raw -echo; fg
   ```

Desta forma, teremos unha shell completamente funcional e lista para traballar tanto en sistemas Linux como Windows.

