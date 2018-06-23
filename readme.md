- ###¿Qué comando utilizaste en el paso 11? ¿Por qué?

		$ git reset --hard HEAD~1
		
		Porque deshace el último commit realizado y por lo tanto lo que había en el Working Copy de manera que todo queda como estaba antes.
		De la misma manera la Staging Area se queda vacía. 
		Desplazamos el puntero HEAD al commit anterior HEAD~1 y el comando reset lo borra y el --hard borra el working copy
		recuperando el anterior.
		
- ###¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?
		
		$ git reflog												(Buscamos el identificador(hash reducido) del commit). En mi caso:
		
			8a36b21 (tag: styled) HEAD@{33}: commit: Modificamos fichero git-nuestro.md en la rama styled	
	
		$ git reset --hard 8a36b21
		
- ###El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?

		No. La historia en la rama styled va por delante de la historia en la rama master. Es decir, el último commit en styled es un sucesor del último 
		commit en master, se trata de una versión mas reciente del fichero y Git no puede eliminar el commit nuevo por el contrario tiene que mantenerlos.
		
- ###El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?

		Sí.Hay dos versiones del fichero, dos archivos han sido editados en la misma línea en dos ramas diferentes y Git no tiene la capacidad de decidir que 
		versión del código en conflicto es la correcta y nos pide que nosotros resolvamos el conflicto de forma nmanual.
		
- ###El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?

		No. Se trata de un merge fast-forward clasico donde la rama master absorbe los commits de la rama styled que no tiene, sin perder sus commits por ello.
		para ello la rama master va a apuntar al mismo commit que la rama styled.
		
- ###¿Qué comando o comandos utilizaste en el paso 25?
	
		$ git graph
		
		El cual es un comando alias del comando git config con los modificadores --graph --decorate --pretty=oneline
	
		$ git config --global alias.graph "log --graph --decorate --pretty=oneline"
	
- ###El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?

		Sí. El grafo de los commits de ambas ramas forman una lista, ya que la rama title contiene un commit que no tiene la rama master y la rama
		master continuaría mantemiendo el trabajo hecho en su rama.
	
- ###¿Qué comando o comandos utilizaste en el paso 27?

		$ git reset HEAD~1

- ###¿Qué comando o comandos utilizaste en el paso 28?

		$ git checkout -- git-nuestro.md
		
- ###¿Qué comando o comandos utilizaste en el paso 29?

		$ git branch -D title

- ###¿Qué comando o comandos utilizaste en el paso 30?
		
		$ git reflog											(Buscamos el identificador(hash reducido) del commit del merge). En mi caso:
			
			72612eb HEAD@{1}: merge title: Merge made by the 'recursive' strategy.
		
		$ git reset --hard 72612eb				(Recupero el Working Copy del commit del merge de la rama title en la rama master)		

- ###¿Qué comando o comandos usaste en el paso 32?
		
		$ git reflog											(Buscamos el identificador(hash reducido) del primer commit). En mi caso:
			
			f298d42 HEAD@{25}: commit (initial): Se sube al repositorio el fichero git-nuestro.md

		$ git reset --hard f298d42				(Recupero el Working Copy del primer commit con el estado original del poema)

- ###¿Qué comando o comandos usaste en el punto 33?

		$ git reflog											(Buscamos el identificador(hash reducido) del commit del merge en la rama master). En mi caso:
			
			72612eb HEAD@{5}: merge title: Merge made by the 'recursive' strategy.

		$ git reset --hard 72612eb				(Recupero el Working Copy del commit del merge de la rama title en la rama master)