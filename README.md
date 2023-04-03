# Selección de algoritmos para composición de un portafolio de inversión en FOREX

## Resumen.
Se busca poder seleccionar sistemas de trading algorítmico generados mediante EA Studio (https://eas.forexsb.com/) basado en la información que se obtienen en la misma página a partir de su creación, posteriormente realizar un backtest sobre los mejores sistemas y finalmente colocarlos en un VPS que tiene la función de ser una “incubadora” para poder evaluar el desempeño de los sistemas con datos en tiempo real. Los sistemas se crean a partir de los dados obtenido por en la página DukasCopy (https://www.dukascopy.com/swiss/spanish/marketwatch/historical/) con un historial de 3 años en el pasado, bajo la condición de que el 90% de la información se usará para la creación/entrenamiento (In Sample) de los sistemas y el 10% de los datos serán fuera de muestra (Out of Sample) sobre los cuales se podrá tener una idea del desempeño de estos; se seleccionará a los mejores. Posteriormente, mediante la herramienta Strategy tester de Meta Trader 4 y el uso de datos del Broker Pepperstone se hará un Backtest para poder obtener métricas de evaluación del sistema y poder comenzar a caracterizarlo; se seleccionarán aquellos que tengan un Calmar mayor o igual a 1.2. Finalmente, los que cumplan con esta métrica se pondrán en funcionamiento en una cuenta demo con un capital que siempre se mantendrá arriba de los 10000USD y todas las estrategias tendrán una 1% de riesgo por operación realizada, a partir del desempeño que estos algorítmos tengan se pretende hacer un análisis completo de datos para seleccionar los mejores sistemas basado en las métricas de evaluación, sus características de generación y su desempeño en el backtest y en operativa en tiempo real, todo esto con objetivo de poder conformar una cartera de inversión automatizada.

## Objetivo
Seleccionar algortimos generados mediante EA Studio en los pares EURUSD, EURJPY, USDJPY, AUDCAD, AUDNZD, GBPCHF en temporalidad de 15 minutos para la composición de un portafolio de inversión automatizado en el mercado de divisas (FOREX).

## Metodología.
1. Generar algoritmos por medio de EA Studio utilizando información de las bases de datos de DukasCopy. Generalmente, para cualquier par en temporalidad de 15 minutos, brinda información de hasta 3 años en el pasado.
    1. Se establecen condiciones que los algoritmos deben cumplir en el tiempo que se estén generando. 
    2. Los algoritmos son generados sobre un 90% de la información siendo el periodo de muestra y 10% de la información siendo el periodo fuera de muestra y deben realizar al menos 200 trades durante todo el periodo de infomración que se tiene.
    3. Se espera, que de forma general, se cumplan al menos 3 condiciones (Aunque a las búsquedas se les puede agregar una o dos condiciones extra, las siguientes tres son las condiciones que permanecen constantes en todas las búsquedas):
        1. R^2 ≥ 65
        2. Profit factor ≥ 1.4
        3. Máximo de pérdidas consecutivas = 5
2. Seleccionar los algoritmos de mejor desempeño acorde a los datos de EA Studio y el comportamiento gráfico que tengan
    1. EA Studio, una vez que genera un algoritmo, brinda una imagen del comportamiento del sistema y cómo el balance de la cuenta fue creciendo o disminuyendo durante el periodo de tiempo establecido
    2. Haciendo uso de una hoja de Excel (RegistroEAStudio), se registran las características que se consideran importantes para evaluar un sistema (también algunas otras que son con el proósito de identificación del sistema que se definirán posteriormente):
        1. Risk/Reward ratio (R/R)  
        2. R^2
        3. Profit Factor
        4. Sharpie Ratio
        5. Sistem Quality Number (SQN)
        6. Max Consecutive Losses
        7. % of Max Drawdown
        8. Win/Loss Ratio (W/L)
        9. Pruebas Montecarlo (Montecarlo)
3. Realizar un backtest por medio de la herramienta Strategy Tester en Meta Trader 4 con información del broker Pepperstone.
    1. Haciendo uso de una hoja de Excel (Aplhatice_Diciembre2022) se registran los resultados obtenidos del backtest teniendo una estimación del posible comportamiento que los sistemas podrían llegar a tener.
    2. A pesar de todos los registros registrados  en la hoja de excel, el filtro para poder poner un algoritmo en funcionamiento  en el VPS para la última fase prueba es que tengan un CALMAR mayor a 1.2.
4. Colorcar en el VPS para un registro de su comportamiento.
    1. Por motivos de manejo de riesgo no se considera prudente pasar un algoritmo a funcionamiento en una cuenta real hasta que se evalue su comportamiento en una cuenta demo durante un cierto periodo de tiempo.
    2. La cuenta demo se mantiene con un capital de 10000 USD para que esté bajo un comportamiento muy parecido al del backtest y la generación en EA Studio, asimismo, se asigna 1% de riesgo por trade a todos los sistemas para poder evaluar de mejor forma sus resultados en profit o pérdida.
    3. El propósito es evaluar el comportamiento de los sistemas a lo largo del tiempo con datos nuevos a diferencia tanto del backtest como de la generación de los sistemas.

## Si desea continuar leyendo sobre el desarrollo del proyecto y una explicación de la implementación de código: [SelecciónAlgoritmosPortafolioFOREX.pdf](https://github.com/3xus/Seleccion-de-algoritmos-para-composici-n-de-un-portafolio-de-inversion-en-FOREX/files/11134800/SeleccionAlgoritmosPortafolioFOREX.pdf)
