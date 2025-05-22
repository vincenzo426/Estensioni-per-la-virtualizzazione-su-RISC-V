# Estensioni per la virtualizzazione su RISC-V
*Università di Bologna - Vincenzo Salvemini*

## 📋 Panoramica
Ho realizzato questo breve documento, per un esame universitario, di approfondimento sulle estensioni di virtualizzazione nell'architettura RISC-V, con focus su hypervisor, gestione della memoria e implementazioni pratiche.

## 🎯 Obiettivi
- Analisi delle tecnologie di virtualizzazione su architettura RISC-V
- Studio delle estensioni hardware specifiche per la virtualizzazione
- Valutazione di implementazioni pratiche (CVA6, Xen)

## 📚 Contenuti Principali

### 1. Virtualizzazione - Fondamenti
- **Hypervisor Tipo 1** (Bare Metal): Xen, VMware ESXi, Hyper-V
- **Hypervisor Tipo 2** (Hosted): VMware Workstation, Oracle VirtualBox
- Vantaggi: ottimizzazione risorse, isolamento, portabilità

### 2. Architettura RISC-V
- **Livelli di privilegio**: Machine Mode (M), Supervisor Mode (S), User Mode (U)
- **Design modulare**: Base ISA + estensioni opzionali
- **Hypervisor Extension**: nuovi livelli HS-mode, VS-mode, VU-mode

### 3. Estensioni per la Virtualizzazione

#### Two-Stage Address Translation
- **VS-Stage**: Guest Virtual → Guest Physical Address
- **G-Stage**: Guest Physical → Host Physical Address
- **Registri chiave**: `vsatp`, `hgatp`

#### Hypervisor CSRs e Istruzioni
- **V-bit**: flag modalità virtualizzazione
- **Istruzioni specializzate**: HLV, HSV, HFENCE
- **Timer extension**: `stimecmp`/`vstimecmp`

### 4. CVA6 Core - Implementazione Pratica
- **Caratteristiche**: pipeline 6 stadi, out-of-order execution
- **Estensioni micro-architetturali**:
  - **GTLB**: Guest TLB per traduzioni intermedie
  - **L2 TLB**: secondo livello set-associative
- **Nested-MMU**: gestione Two-Stage Address Translation

### 5. Xen su RISC-V - Porting in Corso
- **Architettura Xen**: Dom0 (privilegiato) + DomU (guest)
- **Stato del porting**:
  - ✅ Ottimizzazioni codice base
  - ✅ Miglioramenti test e inizializzazione
  - 🔄 Gestione interrupt e Device Tree
  - 🔄 Dom0less e Device Passthrough

## 🎯 Risultati Chiave
- RISC-V offre estensioni native per virtualizzazione efficiente
- Two-Stage Address Translation riduce overhead di traduzione
- CVA6 dimostra implementazione pratica con GTLB e L2 TLB
- Xen su RISC-V promette piattaforma completamente open-source
