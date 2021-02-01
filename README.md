# Relation Network
This is an implementation of Neuro-Symbolic Unification Model.  
If you have any questions or comments, please fell free to contact us by email [rjs951001@gmail.com].

# Data description
data/<DATASETS>/
    train.tsv : train triples
    dev.tsv : dev triples
    test.tsv : test triples
data/<DATASETS>/paths/
    <RELATIONS>.txt : Path Ranking Algorithm을 통해 추출된 Relation Paths
data/<DATASETS>/sentences/
    <RELATIONS>_sentences.txt : Sentence Generator를 통해 생성된 각 Relation의 Sentence Files
data/<DATASETS>/story/
    <RELATIONS>_story.txt : Story Generator를 통해 생성된 각 Relation의 Story Files

# Running
## 1. Sentence Builder

    > python sentenceBuilder.py {kb_path} {relation_list} {pra_output_path} {sentence_output_path}

> **Output Example**
Jeanne_Moreau	/people/person/place_of_birth	inv_/people/person/places_lived./people/place_lived/location	inv_/people/person/nationality	Germany
Albert_Wolsky	/people/person/place_of_birth	inv_/people/person/places_lived./people/place_lived/location	inv_/people/person/nationality	Germany
Roman_Polanski	/people/person/place_of_birth	inv_/people/person/places_lived./people/place_lived/location	inv_/people/person/nationality	Germany

## 2. Story Generator

    > python storyGenerator.py {relation_list} {sentence_output_path} {story_output_path}

> **Output Example**
> 1 Robert_De_Niro inv_/celebrities/celebrity/sexual_relationships./celebrities/romantic_relationship/celebrity inv_/award/award_nominee/award_nominations./award/award_nomination/nominated_for inv_/film/film/language German_Language
2 Robert_De_Niro /people/person/nationality inv_/film/film/release_date_s./film/film_regional_release_date/film_release_region inv_/film/film/language Vietnamese_Language
3 Robert_De_Niro /people/person/nationality inv_/tv/tv_program/country_of_origin inv_/film/film/language Italian_Language
4 Robert_De_Niro /award/award_winner/awards_won./award/award_honor/award_winner inv_/film/film/executive_produced_by inv_/film/film/language English_Language
5 Robert_De_Niro /people/person/nationality inv_/film/film/release_date_s./film/film_regional_release_date/film_release_region inv_/film/film/language German_Language
...
21 Robert_De_Niro /people/person/languages ?	English_Language	4 9 10 13 14 

## 3. A path based relation network learning for knowledge completion

    > python linkPrediction.py {target_relation} {target_story_path} {output_path}

options of linkPrediction.py
[--epochs] = 2, 
[--hidden_dims_g] = [256,256,256], 
[--output_dim_g] = 256, 
[--hidden_dims_f] = [256,512], 
[--hidden_dim_lstm] = 32, 
[--lstm_layers] = 1, 
[--emb_dim] = 32, 
[--batch_size] = 20, 
[--dropout] = True, 
[--only_relevant] = False,
[--weight_decay] = 0,
[--learning_rate] = 1e-4,
[--test_on_test] = True,
[--test_jointly] = False,
[--cuda] = True,
[--load] = False,
[--no_save] = False


> **Output Example**
> david_j /people/person/nationality ? united_kingdom -> united_states_of_america (X) 
terry_crews /people/person/nationality ? united_states_of_america -> united_states_of_america (O) 
william_h._macy /people/person/nationality ? united_states_of_america -> united_states_of_america (O) 
morgan_freeman /people/person/nationality ? united_states_of_america -> united_states_of_america (O) 
david_spade /people/person/nationality ? united_states_of_america -> united_states_of_america (O) 

## The institute to construct dataset
* __The AI Lab in Soongsil University__

## Citation
```
본 연구는 2020년도 정부(과학기술정보통신부)의 재원으로 정보통신기술진흥센터의 지원을 받아 수행된 연구임 
(No.2019000067,대용량 지식그래프 자동완성을 위한 시맨틱 분석 추론기술 개발)
```

