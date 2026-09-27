# Calculadora Digital Basada en ALU de 16 bits
### EIF205 – Arquitectura de Computadoras · Proyecto 1 · Grupo 3

Calculadora digital combinacional de 16 bits implementada en el simulador **Digital**,
con visualización de operador y entrada de signo dinámica.

## Integrantes
- Andrey Chacón Sanchez
- Jorge Navarro Vega
- Keilor Baltodano Martínez

## Variante: Visualización de Operador y Entrada de Signo Dinámica

Esta calculadora extiende el núcleo base con:
- Un decodificador combinacional (**OPDISP**) que muestra en un display de 7 segmentos
  dedicado el símbolo de la operación activa: `+`, `-`, `A` (AND), `O` (OR).
- Un circuito detector de signo (**SIGN**) que activa un display de signo a la extrema
  izquierda cuando el resultado de una operación aritmética es negativo.
- Un conversor a magnitud absoluta (**ABS16**) que muestra el valor en magnitud
  (ej. `-0019`) en vez de su representación cruda en complemento a 2.

## Núcleo Base Común

- Bus de datos de 16 bits (operandos A y B).
- ALU con 4 operaciones seleccionables por `OP[1:0]`: Suma, Resta (complemento a 2),
  AND y OR bit a bit.
- Sumador de acarreo segmentado (*ripple carry*).
- Multiplexor de 16 bits para seleccionar el resultado según `OP`.
- Visualización mediante displays de 7 segmentos.

## Estructura del repositorio
```
ALU16/
├── FA.dig            # Sumador completo de 1 bit
├── ADD4.dig           # 4 FA en cascada
├── ADD16.dig          # Sumador de 16 bits (ripple carry)
├── ADDSUB16.dig       # Suma/resta con XOR y M como Cin
├── LOGIC16.dig        # AND / OR bit a bit de 16 bits
├── ALU16.dig          # Multiplexado del resultado según OP
├── OPDISP.dig         # Decodificador de operador a 7 segmentos
├── SIGN.dig           # Detector de signo del resultado
├── SIGNDISP.dig       # Decodificador de signo a 7 segmentos
├── ABS16.dig          # Conversión a magnitud absoluta
├── MAIN.dig           # Circuito principal (integración completa)
└── Reporte (Keilor, Andrey y Jorge).pdf
```

## Cómo abrirlo

1. Descargar e instalar [Digital](https://github.com/hneemann/Digital).
2. Clonar este repositorio.
3. Abrir `ALU16/MAIN.dig` desde Digital (los demás `.dig` se resuelven automáticamente
   por estar en la misma carpeta).

## Pruebas

El circuito se verificó con el componente *Test Case* de Digital, cubriendo suma, resta
con signo, AND, OR y el caso de desbordamiento (`7FFF + 0001`).

## Curso

Escuela de Informática — Facultad de Ciencias Exactas y Naturales
Arquitectura de Computadoras (EIF205) — Proyecto 1 (15%)
