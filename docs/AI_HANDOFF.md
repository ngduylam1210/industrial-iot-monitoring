# AI Handoff

## Project

Industrial IoT Monitoring & Predictive Maintenance System

## Purpose

Portfolio project focused on:

- Embedded Systems
- Industrial IoT
- Automation

## Current Phase

Phase 1 — Engineering Definition

## Current Status

The project repository and documentation structure have been created.

The following documents are available:

- PROJECT_SPEC.md
- REQUIREMENTS.md
- ARCHITECTURE.md
- DECISIONS.md
- PROJECT_STATE.md
- AI_CONTEXT.md

## Current Architecture

STM32
↓
RS485 / Modbus RTU
↓
ESP32
↓
Wi-Fi / MQTT
↓
Backend
↓
Database
↓
Dashboard
↓
Machine Learning

## Existing Hardware

- STM32
- ESP32

## Important Decisions

- STM32 is the main embedded controller.
- ESP32 is the IoT Gateway.
- RS485 / Modbus RTU is used for industrial communication.
- MQTT is used for IoT communication.
- Real-time processing remains on STM32.
- The project focuses on Embedded + Industrial IoT + Automation.

## Current Task

Establish and validate the multi-AI development workflow.

## Next Task

Begin hardware architecture and BOM planning.

## Instructions for Incoming AI

Before modifying the project:

1. Read this file.
2. Read PROJECT_STATE.md.
3. Read AI_CONTEXT.md.
4. Read the relevant project documentation.
5. Do not redesign existing architecture without discussing it first.
6. Do not guess undocumented information.
7. Continue from the current task instead of restarting the project.

## Handoff

Previous AI:
ChatGPT

Handoff status:
Documentation and AI continuity system established.

Next AI:
Continue from the current task.