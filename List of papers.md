|      | Paper title                                                  | Dataset                                                      | Preprocessing                                                | Algorithm                                                    | Experiment  Results                                          |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1    | Deep Audio-visual  Speech Recognition                        | 1.LRS2     2.LRS3                                            | 1.Generate  the dataset     2.Method of divide the dataset   | 1.Training  Strategy : Curriculum learning     2.Seq2seq      3.CTC | 1.Lip  only (Seq2seq better than CTC)     2.Out-of-sync Audio and Video (Seq2seq is better)     3. Seq2seq vs CTC       3.1Training time (CTC faster than  seq2seq)       3.2Inference time (CTC faster  than seq2seq) |
| 2    | Audio-Visual  Speech Recognition with a Hybrid      CTC/Attention Architecture(2018) | LRS2                                                         | Extract the mouth ROI from      the LRS2 dataset             | 1.ResNet       2.(B)LSTMs     3.CTC     4.RNN-LM             | Audio-visual  model(early fusion) is beteer      than audio-only model |
| 3    | Vggsound: A  lager-scale Audio-Visual Dataset                | Vggsound                                                     |                                                              | 1.Vggish  model      2.ResNet      3.NetVLAD                 | Propose  an automated pipeline for collecting a      large-scale audio-visual dataset – VGGSound. |
| 4    | Learning affective features with  a hybrid deep model for      audio–visual emotion recognition | The acted RML database     the acted eNTERFACE05 database     the     spontaneous BAUM-1s database | 1) Audio Input Generation     2) Visual Input Generation:    | CNN     3D-CNN     DBN                                       | hybrid deep learning     model jointly learns a discriminative audio-visual feature rep-     resentation, which performs better than previous hand-crafted     features and fusion methods on emotion recognition tasks. |
| 5    | A combined rule-based &  machine learning      audio-visual emotion recognition  approach |                                                              | face detection and  localization     Voice Activity Detector (VAD) | PCA     LDA     BDPCA     LSLDA                              |                                                              |
| 6    | Emotion recognition using deep  learning approach      from audio–visual emotional big data | The 2015 Emotion recognition sub-challenge dataset of static  facial expression | CNN                                                          | CNN     ELM                                                  |                                                              |
| 7    | A novel feature set for video emotion recognition            | VACAD，LIRIS-ACCEDE                                          | HHT and the cross-correlation technique                      | HHT                                                          | VACAD: The RMSE of SVR based on the proposed HHTC features is lower than the one based on the traditional features for all six emotions. Thus, the proposed features can outperform previous approaches with statistical significance.<br />LIRIS-ACCEDE: Thus, the computational load will be reduced by more than 70 times compared with the traditional feature extraction processes. |
| 8    | Emotion Recognition Using Fusion of Audio and Video Features | RECOLA<br />FER                                              | CNN                                                          | CNN                                                          |                                                              |
| 9    |                                                              |                                                              |                                                              |                                                              |                                                              |

