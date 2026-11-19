# Пример 04 — таймер и PWM

Заготовка практической работы к [лекции 4](../../lectures/04_timers_pwm.md) для STM32F407 + STM32CubeIDE + HAL C.
Частоты рассчитаны для SYSCLK = 168 МГц (таймеры APB1 тактируются 84 МГц). Если у вас другие настройки — пересчитайте PSC и ARR.

## Настройка в CubeMX
1. **TIM6**: Activated, Prescaler = 8399, Counter Period = 9999 (1 Гц), NVIC — включить TIM6 global interrupt.
2. **PWM**: вывод светодиода, у которого есть функция `TIMx_CHy`, назначить этой функции.
   Для TIMx (на APB1): Channel = PWM Generation, Prescaler = 83, Counter Period = 999 (1 кГц), Pulse = 0.
3. Проверьте, что выбранные таймеры не совпадают с SYS → Timebase Source.
4. Сгенерируйте код.

## Код пользовательской части

Глобальные переменные (`USER CODE BEGIN PV`):

```c
volatile uint8_t tick1s = 0;
```

Запуск (`USER CODE BEGIN 2`):

```c
HAL_TIM_Base_Start_IT(&htim6);
HAL_TIM_PWM_Start(&htim4, TIM_CHANNEL_1);   /* замените на свой таймер и канал */

uint32_t fadeTick = HAL_GetTick();
uint16_t duty = 0;
int8_t step = 10;
```

Основной цикл (`USER CODE BEGIN 3`):

```c
if (tick1s != 0)
{
    tick1s = 0;
    HAL_GPIO_TogglePin(LED2_GPIO_Port, LED2_Pin);   /* второй светодиод, раз в секунду */
}

if (HAL_GetTick() - fadeTick >= 10U)
{
    fadeTick += 10U;
    duty += step;
    if (duty >= 1000U || duty == 0U)
    {
        step = -step;
    }
    __HAL_TIM_SET_COMPARE(&htim4, TIM_CHANNEL_1, duty);
}
```

Callback (`USER CODE BEGIN 4`). Если `HAL_TIM_PeriodElapsedCallback()` уже есть в main.c (Timebase на таймере), добавьте ветку в существующую функцию:

```c
void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim)
{
    if (htim->Instance == TIM6)
    {
        tick1s = 1;
    }
}
```

Замените имена `htim4`, `TIM_CHANNEL_1`, `LED2_*` на созданные в вашем проекте. Это фрагменты кода, а не готовый проект: файл .ioc и разводка платы не включены.
