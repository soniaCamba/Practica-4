# Practica-4

# Practica 4A

## CODIGO
```
#include <Arduino.h>

void anotherTask( void * parameter );
void setup()
{
    Serial.begin(115200);
    /* we create a new task here */
    xTaskCreate(anotherTask, "another Task", 10000, NULL, 1, NULL); /* Task handle to keep track of created task */
}
 
/* the forever loop() function is invoked by Arduino ESP32 loopTask */
void loop()
{
    Serial.println("this is ESP32 Task");
    delay(1000);
}
 
/* this function will be invoked when additionalTask was created */
void anotherTask( void * parameter )
{
    /* loop forever */
    for(;;)
    {
        Serial.println("this is another Task");
        delay(1000);
    }
    /* delete a task when finish,
    this will never happen because this is infinity loop */
    vTaskDelete( NULL );
}
```
## FUNCIONAMIENTO

```
 Serial.begin(115200);
    /* we create a new task here */
    xTaskCreate(anotherTask, "another Task", 10000, NULL, 1, NULL); /* Task handle to keep track of created task */
```
> anotherTask: Nombre del subprograma que hay que llamar.
> another Task: Nombre del subrograma.
> 10000: Tamaño (bytes).
> NULL: Parametro a pasar.
> 1: Prioridad de la tasca (puede variar entre 1-24).
> NULL: Identificador de tareas.

## PREGUNTAS
### ¿qué sucede si está utilizando una pantalla de tinta electrónica que tarda unos segundos en actualizarse?
Que si la nueva orden tarda menos en ejecutarse, la pantalla no estaria sincronizada con el propio programa que se esta ejecutando.
