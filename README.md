# STM32 Course / Курс STM32

**Platform / Платформа:** STM32F407 · STM32CubeIDE · STM32 HAL C  
**Audience / Аудитория:** Developers who know C and are new to STM32 / Разработчики, знающие C и начинающие изучать STM32.

## Русский

Открытый учебный курс по разработке встроенных систем на STM32F407. Материалы включают лекции, схемы, примеры HAL C, практические задания и контрольные вопросы.

### Содержание
1. [Лекция 1 — Знакомство с STM32](01_introduction.md)
2. Лекция 2 — Проект в STM32CubeIDE и работа с GPIO (материал готовится к публикации)
3. [Лекция 3 — Внешние прерывания EXTI и NVIC](lectures/03_exti_nvic.md)
4. Лекция 4 — Таймеры и PWM (следующая)
5. Лекция 5 — UART и DMA

### Как использовать
- Читайте лекции в папке `lectures/`.
- Примеры практических работ находятся в `examples/`.
- Материалы для LinkedIn — в `linkedin/`.

**Важно:** примеры требуют проверки на конкретной плате. Назначение выводов светодиода зависит от модели платы. Не подключайте внешние цепи без проверки напряжений и схемы платы.

## English

An open educational course on embedded development with STM32F407. Materials include lessons, diagrams, HAL C examples, practical exercises, and review questions.

### Contents
1. [Lesson 1 — Introduction to STM32](01_introduction.md)
2. Lesson 2 — STM32CubeIDE project and GPIO (prepared for publication)
3. [Lesson 3 — External interrupts EXTI and NVIC](lectures/03_exti_nvic.md)
4. Lesson 4 — Timers and PWM (next)
5. Lesson 5 — UART and DMA

### How to use
- Read lessons in `lectures/`.
- Practical examples are stored in `examples/`.
- LinkedIn-ready drafts are stored in `linkedin/`.

**Note:** verify examples against your exact development board. The LED pin varies by board model. Check voltage levels and the board schematic before wiring external circuits.

## Contribution / Участие

Issues and pull requests with corrections, improvements, and tested examples are welcome. Please state the exact STM32 part number, board, STM32CubeIDE version, and test conditions.

## License / Лицензия

See [LICENSE](LICENSE). The code and text are provided for educational purposes; verify third-party library licenses separately.
