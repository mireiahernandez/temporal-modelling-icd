# temporal-modelling-icd

Temporal modelling ICD-9 code predictions.

This repository contains the code for the paper "Towards Real-Time Medical Coding: Temporal ICD-9 Code Prediction
from Electronic Health Records."

To reproduce the results, run the main file with the following arguments:

python main.py \
    --num_chunks 16 \
    --run_name MMULA_evaluate \
    --max_epochs 20 \
    --num_heads_labattn 1 \
    --patience_threshold 3 \
    --debug False \
    --evaluate_temporal True \
    --use_multihead_attention True \
    --weight_aux 0 \
    --num_layers 1 \
    --num_attention_heads 1 \
    --setup random \
    --limit_ds 0 \
    --is_baseline False \
    --aux_task "none" \
    --use_all_tokens False \
    --apply_transformation False \
    --apply_weight False \
    --reduce_computation True \
    --apply_temporal_loss False \
    --save_model True

Quick explanation about important arguments
--setup: it can take values random, last, uniform. ``random`` refers to applying the ECA algorithm, using random sampling during training and processing the entire sequence during inference. ``uniform`` refers to ablating the ECA algorithm and selecting $N$ random chunks. ``last" refers to ablating the ECA algorithm and selecting the last $N$ chunks.
--evaluate_temporal (True or False): whether to report performance at various temporal cut-offs
--num_chunks: how many chunks to process
--weight_aux, aux_task, apply_transformation, apply_weight: these are legacy arguments from another project that aimed to apply auxiliary tasks for ICD coding (please disregard them)
--num_layers, num_attention_heads: masked (hier) transformer hyperparameters
--num_heads_labattn: number of heads in the label attention module
--use_multihead_attention: whether to use multihead attention or the classic label attention


