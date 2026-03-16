---
id: taskmanager-cron
aliases: []
tags: []
---

finalize-orders -> http://localhost:80/api/v1/prd/finalize_orders/10 -> todo dia as 5 da manhã
apontamento PA -> script -> C:APPS/RFiD/PRD/ApontamentoPA.ps1 -Timeout 60 -> todo dia a cada 5 minutos
apontamento de acabados -> get -> http://localhost:80/api/v1/prd/send_appointment_finishgoods_job/15 -> todo dia a cada 15 minutos
documento transporte -> http://localhost:80/api/v1/clean_documento_transporte -> todo dia as 6 da manhã
handle production order activation -> http://localhost:80/api/v1/prd/handle_production_order_activation -> todo dia a cada 1 minuto
sincronização de carga batida -> http://localhost:80/api/v1/synchronize_track_items -> todo dia a cada 5 minutos
sincronização de pallets -> http://localhost:80/api/v1/check_not_synced_pallets -> todo dia a cada 5 minutos
