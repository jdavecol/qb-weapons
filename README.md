# qb-weapons
Weapon Logic Script For QB-Core — Modified for PLGC Server

## Descripción

Script de lógica de armas para el framework QBCore. Maneja eventos de armas, daño, durabilidad, munición, attachments y recarga.

Esta versión incluye modificaciones personalizadas aplicadas al servidor **PLGC**.

---

## Modificaciones DSCO

### 🔫 Recarga con tecla R
Se agregó soporte para recargar el arma presionando **R** directamente, sin necesidad de asignar la munición a un slot del hotbar ni presionar su número.

- Al presionar **R** con un arma en mano, el sistema detecta automáticamente el tipo de munición compatible
- Busca en el inventario del jugador el item de balas correspondiente (en cualquier slot)
- Ejecuta el mismo flujo de recarga que al usar el item manualmente (barra de progreso + consume el item)
- Archivos modificados: `client/weapdraw.lua`, `server/main.lua`

### 🔴 Munición por paquete ajustada
Se corrigió la cantidad de balas que otorga cada paquete de munición de pistola.

- **Antes:** 1 paquete = 30 disparos
- **Ahora:** 1 paquete = 12 disparos (1 cartucho)
- Aplica a: `pistol_ammo` (pistola, pistola .50, water pistol y cualquier arma con `AMMO_PISTOL`)
- Archivo modificado: `config.lua`

---

## Características base

- Manejo de eventos de armas
- Sistema de durabilidad con degradación configurable por arma
- Lógica de recarga con barra de progreso
- Soporte de attachments por arma
- Tints (colores) para armas normales y MK2
- Sistema de reparación de armas en punto físico
- Animaciones de holster al sacar/guardar arma (`weapdraw.lua`)
- Retroceso (recoil) personalizado por arma (`recoil.lua`)
- Integración con `qb-inventory`, `qb-phone`, `qb-core`

---

## Configuración rápida

```lua
-- config.lua
Config.ReloadTime = math.random(4000, 6000) -- tiempo de recarga en ms

Config.AmmoTypes = {
    pistol_ammo  = { ammoType = 'AMMO_PISTOL',     amount = 12 }, -- PLGC: 12
    rifle_ammo   = { ammoType = 'AMMO_RIFLE',       amount = 30 },
    smg_ammo     = { ammoType = 'AMMO_SMG',         amount = 30 },
    shotgun_ammo = { ammoType = 'AMMO_SHOTGUN',     amount = 10 },
    mg_ammo      = { ammoType = 'AMMO_MG',          amount = 30 },
    snp_ammo     = { ammoType = 'AMMO_SNIPER',      amount = 10 },
    emp_ammo     = { ammoType = 'AMMO_EMPLAUNCHER', amount = 10 },
}
```

---

## Dependencias

- [qb-core](https://github.com/qbcore-framework/qb-core)
- [qb-inventory](https://github.com/qbcore-framework/qb-inventory)
- [qb-phone](https://github.com/qbcore-framework/qb-phone)

---

## Licencia

    QBCore Framework
    Copyright (C) 2021 Joshua Eger

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>
