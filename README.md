# Targeted Universal Adversarial Perturbations to End-to-end ASR Models

Authors: {zhiyunlu,weihan,ngyuzh,llcao}@google.com

This pages demonstrates some examples of targeted universal adversarial
perturbations to e2e ASR models. Details can be found in the paper
[Exploring Targeted Universal Adversarial Perturbations to End-to-end ASR Models](https://arxiv.org/abs/2104.02757).

[TOC]

## Abstract

![alt_text](universal_attack.png "universal targeted adversarial examples"){height="275" style="float: right"}
Although end-to-end automatic speech recognition (e2e ASR) models are widely
deployed in many applications, there have been very few studies to understand
models' robustness against adversarial perturbations. In this work, we explore
whether a targeted universal perturbation vector exists for e2e ASR models. Our
goal is to find perturbations that can mislead the models to predict the given
targeted transcript such as "thank you" or empty string on any input utterance.

We study two different attacks, namely additive and prepending perturbations,
and their performances on the state-of-the-art LAS, CTC and RNN-T models. We
find that LAS is the most vulnerable to perturbations among the three models.
RNN-T is more robust against additive perturbations, especially on long
utterances. And CTC is robust against both additive and prepending
perturbations. To attack RNN-T, we find prepending perturbation is more
effective than the additive perturbation, and can mislead the models to predict
the same short target on utterances of arbitrary length.

## Audio-agnostic adversarial examples

There are two sets of results in this page, one from
[*prepending perturbation*](#id-pp) and the other from
[*additive perturbation*](#id-add). For each type of perturbation, we show the
results for LAS and RNN-T models and omit CTC models' as attack to CTC is not
successful. Please refer to paper Section 2.3 for LAS and RNN-T model details.

In each table, the "universal perturbation" row shows the waveform and the audio
of the learnt perturbation vector reported in Table 2 and 4 of the paper. The
"perturbed utterance" rows are randomly selected utterances which are
successfully attacked, i.e. the ASR prediction is the given target. The original
utterance is from LibriSpeech test-clean set, and the attack has never seen
these utterances during training. In the waveform plots, we use blue color to
represent the clean signal, and the orange color for the perturbed signal.

### Prepending perturbation{#id-pp}

- <h6> target transcript is empty string.</h6>
The success rates on the Librispeech test-clean and test-others are 99.54% / 99.39% for LAS,
and 41.18% / 47.43% for RNN-T. Please see Table 4 in the paper for more details.

| | LAS | RNN-T
---------- | :--------: | :---:
    <h5>universal perturbation</h5>  | <g3mark-audio url="audios/las_pp_empty.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_pp_empty.png "waveform of las prepend perturbation")    | <g3mark-audio url="audios/rnnt_pp_empty.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_pp_empty.png "waveform of rnnt prepend perturbation")
    <h5>perturbed utterance 1</h5>   <h6>original transcript: </h6> he hoped there would be stew for dinner turnips and carrots and bruised potatoes and fat mutton pieces to be ladled out in thick peppered flour fattened sauce   <h6>ASR prediction = ""</h6> | <g3mark-audio url="audios/las_pp_empty_utt1.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_pp_empty_utt1.png "waveform of las perturbed utt") | <g3mark-audio url="audios/rnnt_pp_empty_utt1.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_pp_empty_utt1.png "waveform of rnnt perturbed utt")
    <h5>perturbed utterance 2</h5>  <h6>original transcript: </h6>  a cold lucid indifference reigned in his soul <h6>ASR prediction = ""</h6>   | <g3mark-audio url="audios/las_pp_empty_utt2.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_pp_empty_utt2.png "waveform of las perturbed utt") | <g3mark-audio url="audios/rnnt_pp_empty_utt2.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_pp_empty_utt2.png "waveform of rnnt perturbed utt")

- <h6> target transcript is "thank you".</h6>

The success rates on the Librispeech test-clean and test-others are 99.92% / 99.93% for LAS,
and 35.65% / 37.80% for RNN-T. Please see Table 4 in the paper for more details.

| | LAS   | RNN-T
---------- | :--------: | :---:
    <h5>universal perturbation</h5>  | <g3mark-audio url="audios/las_pp_thank_you.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_pp_thank_you.png "las thank you")  | <g3mark-audio url="audios/rnnt_pp_thank_you.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_pp_thank_you.png "rnnt thank you")
    <h5>perturbed utterance 1</h5>   <h6>original transcript: </h6> he hoped there would be stew for dinner turnips and carrots and bruised potatoes and fat mutton pieces to be ladled out in thick peppered flour fattened sauce   <h6> ASR prediction = "thank you"</h6> | <g3mark-audio url="audios/las_pp_tu_utt1.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_pp_tu_utt1.png "waveform of las perturbed utt")  | <g3mark-audio url="audios/rnnt_pp_tu_utt1.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_pp_tu_utt1.png "waveform of rnnt perturbed utt")
<h5>perturbed utterance 2</h5>   <h6>original transcript: </h6>  a cold lucid indifference reigned in his soul  <h6>ASR prediction = "thank you" </h6> | <g3mark-audio url="audios/las_pp_tu_utt2.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_pp_tu_utt2.png "waveform of las perturbed utt") | <g3mark-audio url="audios/rnnt_pp_tu_utt2.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_pp_tu_utt2.png "waveform of rnnt perturbed utt")


### Additive perturbation{#id-add}

Note additive perturbation on RNN-T is not as successful as prepending perturbation.

- <h6> target transcript is empty string.</h6>
The success rates on the Librispeech test-clean and test-others are 99.35% / 99.66% for LAS,
and 14.66% / 19.02% for RNN-T. Please see Table 2 in the paper for more details.

| | LAS   | RNN-T
---------- | :--------: | :---:
     <h5> universal perturbation</h5>   | <g3mark-audio url="audios/las_add_empty.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_add_empty.png "las additive perturbation of empty target")   | <g3mark-audio url="audios/rnnt_add_empty.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_add_empty.png "rnnt additive perturbation of empty target")
    <h5>perturbed utterance 1</h5>  <h6>original transcript: </h6> whose feet are as the feet of harts and underneath the everlasting arms  <h6>ASR prediction = ""</h6> | <g3mark-audio url="audios/las_add_empty_utt1.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_add_empty_utt1.png "las additive perturbation perturbed utt") | <g3mark-audio url="audios/rnnt_add_empty_utt1.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_add_empty_utt1.png "rnnt additive perturbation perturbed utt")
  <h5>perturbed utterance 2</h5>  <h6>original transcript:</h6> stuff it into you his belly counselled him <h6>ASR prediction = ""  | <g3mark-audio url="audios/las_add_empty_utt2.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_add_empty_utt2.png "las additive perturbation perturbed utt") | <g3mark-audio url="audios/rnnt_add_empty_utt2.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_add_empty_utt2.png "rnnt additive perturbation perturbed utt")


- <h6> target transcript is "thank you".</h6>
The success rates on the Librispeech test-clean and test-others are 98.74% / 99.52% for LAS,
and 1.85% / 2.75% for RNN-T. Please see Table 2 in the paper for more details.


| | LAS    | RNN-T
--- | :--------: | :---:
    <h5> universal perturbation </h5> | <g3mark-audio url="audios/las_add_thank_you.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_add_thank_you.png "las additive perturbation of thank you target") | <g3mark-audio url="audios/rnnt_add_thank_you.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_add_thank_you.png "rnnt additive perturbation of thank you target")
    <h5>perturbed utterance 1 </h5>  <h6>original transcript: </h6> whose feet are as the feet of harts and underneath the everlasting arms <h6>ASR prediction = "thank you"</h6> | <g3mark-audio url="audios/las_add_tu_utt1.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_add_tu_utt1.png "las additive perturbation perturbed utt") | <g3mark-audio url="audios/rnnt_add_tu_utt1.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_add_tu_utt1.png "rnnt additive perturbation perturbed utt")
  <h5>perturbed utterance 2 </h5> <h6>original transcript: </h6> tis now winter out of doors thought the tree <h6>ASR prediction = "thank you"</h6> | <g3mark-audio url="audios/las_add_tu_utt2.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/las_add_tu_utt2.png "las additive perturbation perturbed utt") | <g3mark-audio url="audios/rnnt_add_tu_utt2.wav" description_style="text-align: center;"></g3mark-audio> ![alt_text](waveforms/rnnt_add_tu_utt2.png "rnnt additive perturbation perturbed utt")
