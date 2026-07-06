# Ejercicio Nro: 1

## Enunciado
Tu tarea es desarrollar una aplicación informática utilizando la técnica TDD para gestionar una cuenta bancaria. La aplicación debe permitir a los usuarios abrir una cuenta, realizar depósitos, hacer retiros y transferir fondos entre cuentas.

## Resolución
Para resolver este ejercicio aplicando TDD, utilizamos la librería nativa `unittest` de Python. Primero se escribieron las pruebas automatizadas (fase roja), luego se implementó el código mínimo necesario para que pasaran (fase verde) y finalmente se optimizó la estructura (fase de refactorización). 

A continuación se presenta el código resultante dividido en dos archivos (Pruebas e Implementación).

### 1. Archivo de Pruebas (`test_cuenta_bancaria.py`)
Este archivo cubre las **Etapas 1, 2, 3 y 4**, verificando desde la creación básica hasta los casos límite (excepciones), utilizando la estructura Arrange, Act, Assert.

```python
import unittest
from cuenta_bancaria import CuentaBancaria

class TestCuentaBancaria(unittest.TestCase):
    
    # Se ejecuta antes de cada test para preparar el estado (Arrange)
    def setUp(self):
        self.cuenta_a = CuentaBancaria(1000) # Cuenta con $1000
        self.cuenta_b = CuentaBancaria(500)  # Cuenta con $500

    # ETAPA 1: Especificación y prueba inicial
    def test_crear_cuenta_y_obtener_saldo(self):
        self.assertEqual(self.cuenta_a.obtener_saldo(), 1000)

    # ETAPA 2: Desarrollo de funcionalidades básicas
    def test_depositar(self):
        self.cuenta_a.depositar(500)
        self.assertEqual(self.cuenta_a.obtener_saldo(), 1500)

    def test_retirar(self):
        self.cuenta_a.retirar(200)
        self.assertEqual(self.cuenta_a.obtener_saldo(), 800)

    def test_transferir(self):
        self.cuenta_a.transferir(self.cuenta_b, 300)
        self.assertEqual(self.cuenta_a.obtener_saldo(), 700) # 1000 - 300
        self.assertEqual(self.cuenta_b.obtener_saldo(), 800) # 500 + 300

    # ETAPAS 3 y 4: Pruebas adicionales, casos límite y excepciones
    def test_retirar_fondos_insuficientes(self):
        with self.assertRaises(ValueError) as context:
            self.cuenta_a.retirar(2000)
        self.assertTrue("Fondos insuficientes" in str(context.exception))

    def test_transferir_cuenta_invalida(self):
        with self.assertRaises(ValueError):
            self.cuenta_a.transferir(None, 100)

    def test_depositar_monto_invalido(self):
        with self.assertRaises(ValueError):
            self.cuenta_a.depositar(-50)

if __name__ == '__main__':
    unittest.main()
```
```python
2. Archivo de Implementación (cuenta_bancaria.py)
Este es el código de producción que se fue escribiendo y refactorizando gradualmente para lograr que todos los tests anteriores se ejecuten correctamente y pasen a verde.
class CuentaBancaria:
    def __init__(self, saldo_inicial=0):
        self.saldo = saldo_inicial

    def obtener_saldo(self):
        return self.saldo

    def depositar(self, monto):
        # Etapa 4: Manejo de casos límite
        if monto <= 0:
            raise ValueError("El monto debe ser mayor a cero.")
        self.saldo += monto

    def retirar(self, monto):
        # Etapa 3: Prueba adicional de control de fondos
        if monto > self.saldo:
            raise ValueError("Fondos insuficientes.")
        self.saldo -= monto

    def transferir(self, cuenta_destino, monto):
        # Etapa 3: Prueba adicional de cuenta inexistente
        if cuenta_destino is None:
            raise ValueError("La cuenta destino no es válida.")
        
        # Etapa 3: Refactorización -> Se reutilizan los métodos retirar y depositar 
        # para no duplicar código y mantener un diseño simple y cohesivo.
        self.retirar(monto)
        cuenta_destino.depositar(monto)
```
