---
title: "Do it 쉽게 배우는 <font color='orange'> R</font> 데이터 분석"
categories:
    - data-science
tags:
    - data-science
    - R
toc: true
---

# "Do it 쉽게 배우는 <font color='orange'> R</font> 데이터 분석"


## 1. R 환경설정 (1~2장)

 - 교재 소스 코드 : https://github.com/youngwoos/Doit_R/#start_r
 - 교재 강의안 : https://github.com/youngwoos/Doit_R/tree/master/Lecture
 - R 다운로드 : https://cran.r-project.org/mirrors.html / https://cran.seoul.go.kr/
 - R 스튜디오 다운로드 : https://www.rstudio.com/products/rstudio/download
   *(주의) R 스튜디오 실행시 오류 발생하면 관리자 권한으로 실행*

> **R 스튜디오 사용법**
>1. ctrl+Enter : 소스 실행
>2. 범위 선택 + ctrl+Enter : 여러줄 소스 실행
>3. 변수 대입 방법 : a <- 1 
>4. 신규프로젝트 생성 => .Rproj 파일이 생성됨
>5. 소스창에서 저장(ctrl+S) => .R 파일이 생성됨
>6. R스튜디오 자동저장 : .RData 파일로 자동저장됨
>7. Tools - Global Options : R 스튜디어 전반에 영향을 주는 옵션
>8. Tools - Project Options : 프로젝트가 열린 상태에만 영향 주는 옵션
>9. Soft-wrap 자동 줄바꿈 옵션 : Tools-Global Options-Code탭
>10. UTF-8 설정 : Toos-Project Options-Code Editing탭
>11. 주석처리 : # 사용



## 2. R 기본문법 : 변수, 함수, 패키지 (3장)

>변수

    var1 <- c(1,2,5,7,8) 		# 숫자 5개로 구성된 배열 va1 생성
    var2 <- c(1:5) 				# 1~5까지 연속 값으로 var2 생성
    var3 <- seq(1,5) 			# 1~5까지 연속 값으로 var3 생성
    var4 <- seq(1,10,by=2) 		# 1~10까지 2 간격 연속 값으로 var4 생성
    var1+2 						# 각 값에 +2 연산을 함
    var1+var2 					# var1과 var2 각 값에 + 연산시행
    str1 <- "a"					# 문자열
    str2 <- "Hello World!"
    str3 <- c("a","b","c") 		# 문자열 배열
    str1+2 						# Error : 문자열은 연산 불가
  

>함수

    #변수 만들기
    x <- c(1,2,3)
    mean(x) 		#함수 적용하기
    ## [1] 2    	#결과
    max(x)
    ## [1] 3    	#결과
    min(x)
    ## [1] 1    	#결과
    paste(str, collapse=",")  	#쉼표를 구분자로 str5의 단어를 하나로 합치기
    ## [1] "Hello!,Wolrd,is,good!"
    paste(str, collapse=" " )  	
    ## [1] "Hello! Wolrd is good!"
    str_paste <- paste(str, collapse=" " )  	
>패키지

    🔸패키지 인스톨 : [콘솔창에서] >install.packages("KONLP")
	  에러시 참조 : [https://r-pyomega.tistory.com/12](https://r-pyomega.tistory.com/12)
	🔸패키지 경로 확인 : >.libPaths()
	🔸패키지 업데이트 : >update.packages()
	🔸패키지 삭제 : remove.pakages("대상")
	🔸패키지 사용 : library("패키지명")
	🔸현재 디렉토리 확인 : getwd()
	🔸디렉토리 변경 : setwd("c:\\temp")
	🔸R내장 함수 확인 : help(package=base)
	🔸패키지 함수 확인 : help(package="KoNLP")
	🔸변수타입 확인 : class( 변수명 )
	🔸?qplot : 함수에 대한 도움말
	🔸?ggplot2 : 패키지에 대한 도움말

## 3. 데이터 프레임 (4장)

>**엑셀파일 불러오기**

    library(readxl)
    df_exam <- read_excel("excel_exam.xlsx", col_names = F) # 첫행이 열 이름이 아니다 (False)
    df_exam_sheet <-read_excel("excel_exam_sheet.xlsx", sheet = 3) # sheet 3 불러오기
    df_csv_exam <-read.csv("csv_exam.csv", stringsAsFactors = F) # 문자가 있는 csv를 불러올 때는 stringsAsFactors 를 F로 설정해 줘야 함.


>**데이터 프레임 만들기**

    df_midterm <- data.frame(english=c(90,80,60,70), 
    						math = c(50,60,100,20),
							class = c(1,1,2,2,))
	write.csv(df_midterm, file="df_midterm.cvs")

>**RDS(R 전용 데이터 파일) 파일 활용하기**

    saveRDS(df_midterm, file="df_midterm.rds")
    rm(df_midterm) # 데이터 프레임 삭제
    df_midterm <- readRDS("df_midterm.rds")

> **분석하기**

    mean(df_exam$english)
    ## [1] 84.9
	mean(df_exam$science)
	## [1] 59.45
	
## 4. 데이터 분석 기초 (5장)
### 데이터 파악하기, 다루기 쉽게 수정하기
>**기술 통계 함수들**

|함수|기능|예시|
|--|--|--|
|head()  |데이터 앞부분 출력  		|head(exam,10)  |
|tail()  |데이터 뒷부분 출력  		|tail(exam,5)|
|View()  |뷰어 창에서 데이터 확인  |View(exam)  |
|dim()  |데이터 차원 출력  		|dim(exam)|
|str()  |데이터 속성 출력  		|str(exam)|
|summary()  |요약 통계량 출력  		|summary(exam)|

>**변수명 바꾸기**

    df_raw <- data.frame(var1 = c(1,2,1), var2 = c(2,3,2))
    df_new <- rename(df_raw, v2=var2)     		#dataframe의 var2변수가 v2로 변경됨

>**파생 변수 만들기**

    df_new$total <- (df_new$va1 + df_new$v2)
    df_new$avr <- (df_new$total) /2

>**히스토그램 생성**

    hist(df_new$total)

>**qplot 활용**

    qplot(df_new$total) # 간단한 막대그래프로 데이터 확인

>**ifelse()문 사용하기**

    #A,B,C,D 등급 부여
    mpg$grade2 <- ifelse(mpg$total >= 30, "A",
				    ifelse(mpg$total>=25,"B",
					    ifelse(mpg$total>=20,"C","D")))

## 5. 데이터 프레임 가공하기 (6장)

>**dplyr 패키지** : 데이터 전처리 작업에 가장 많이 사용되는 패키지

|dplyr함수|기능  |
|--|--|
|filter()  |행 추출  |
|select()  |열(변수) 추출  |
|arrange()  |정렬 |
|mutate()  |변수 추가  |
|summarise()  |통계치 산출  |
|group_by()  |집단별로 나누기  |
|left_join()  |데이터 합치기(열) |
|bind_rows()  |데이터 합치기(행) |
|%>%  |파이프라인 (오른쪽으로 데이터 넘김) |

>**summarise()** 통계량 함수

|함수|의미  |
|--|--|
|mean()  |평균  |
|sd()  |표준편차  |
|sum()  |합계  |
|median()  |중앙값  |
|min()  |최솟값  |
|max()  |최댓값  |
|n()  |빈도  |

## 6. 데이터 정제 (7장)
> 결측치 확인

    is.na(df) 			# 결측치 확인
    table(is.na(df)) 	# 결측치 빈도 출력

>결측치 제거

    df<-df %>% filter(!is.na(score))  # score 결측치 제거

> 모든 변수에 결측치 없는 데이터 추출

    df <- na.omit(df)  # 한번에 처리

> 결측치 대체하기

    exam$math <- ifelse(is.na(exam$math),55,exam$math)
    mean(exam$math, na.rm=T) # 결측치 제외하고 math 평균 산출

> 이상치 확인하기

    table(outlier$score) # 값과 빈도수 확인

> 이상치를 결측치로 변환

    outlier$score <- ifelse(outlier$score > 5, NA, outlier$score)


## 7. 그래프 시각화 (8장)
그래프 부분은 이 교재 보다 아래의 링크에 설명이 더 자세하다
https://wikidocs.net/33957 :: 논문 작성에 필요한 R ggplot2 시각화

## 8. 텍스트 마이닝 (10장)
1. 패키지 준비하기
    `library(KoNLP)		#한글 자연어 분석 패키지`
    `library(dplyr)		#전처리 작업 패키지`

2. 사전 설정하기
	`useNIADic()			#행태소 분석을 위한 사전`

3. 데이터 준비하기
	`txt <- readLines("hiphop.txt)" 	# 분석 대상 텍스트`  

4. 데이터 정제 (특수문자 제거하기)
	`library(stringr)`
	`txt<-str_replace_all(txt,"\\W", " ") 	# "\\W" 은 정규식 표현`

5. 명사 추출하기
	`nouns <- extractNoun(txt)	#가사에서 명사 추출`
	`wordcount <- table(unlist(nouns))	#추출한 명사 list를 문자열 벡터로 변환, 단어별 빈도표 생성`
	`df_word <- as.data.frame(wordcount, stringsAsFactors=F) #데이터 프레임으로 변환`
	`df_word <- rename(df_word, word=Var1, freq=Freq) #변수명 수정`

6. 자주 사용된 단어 빈도표 만들기
	`df_word <-filter(df_word, nchar(word)>=2) 	#두 글자 이상 단어 추출`

7. 워드클라우드 준비 - 패키지 
	`library(wordcloud)	`
	`library(RColorBrewer)	#색상목록을 만들어 주는 팔레트`
	
8. 단어 색상 목록 만들기
	`pal <- brewer.pal(8,"Dark2") #Dark2 색상 목록에서 8개 색상 추출`
	
9. 난수 고정하기
	`set.seed(1234) 	#매번 실행시 다른 모양의 WC 만들기 위해 난수 설정`

10. 워드 클라우드 실행
>
		    wordcloud(	words = df_word$word, 		#단어
					    freq = df_word$freq,		#빈도
					    min.freq = 2,				#최소 단어 빈도
					    max.words = 200,			#표현 단어 수
					    random.order = F,			#고빈도 단어 중앙 배치
					    rot.per = .1,				#회전 단어 비율
					    scale = c(4,0.3),			#단어 크기 범위
					    colors = pal	)			#색상 목록

![enter image description here](https://files.slack.com/files-pri/T01EXPUN88H-F01FVA3UDRR/image.png)

[예제] 국정원 트윗 텍스트 마이닝

    library(KoNLP)
    library(dplyr)
    library(stringr)
    library(wordcloud)
    library(RColorBrewer)
    library(ggplot2)
    twitter <-read.csv("twitter.csv", header=T, stringsAsFactors=F,fileEncoding="UTF-8")
    twitter <-rename(twitter, no=번호, id=계정이름, date=작성일, tw=내용)
    twitter$tw <- str_replace_all(twitter$tw, "\\W", " ")
    nouns <-extractNoun(twitter$tw)
    wordcount <-table(unlist(nouns))
    df_word <-as.data.frame(wordcount, stringsAsFactors=F)
    df_word <-rename(df_word, word=Var1, freq=Freq)
    df_word <- filter(df_word, nchar(word) >= 2)
    top20 <- df_word %>% arrange(desc(freq)) %>% head(20)
    order <- arrange(top20, freq)$word
    ggplot(data=top20, aes(x=word,y=freq)) +
      ylim(0,2500) +
        geom_col() +
        coord_flip() +
        scale_x_discrete(limit=order) + 
        geom_text(aes(label=freq), hjust=-0.3)
![enter image description here](https://files.slack.com/files-pri/T01EKBCJJ8K-F01G7R8KVU1/image.png)

 install.packages("tm")   ?????


## 9. 프로젝트 내용 (어린이 사고 vs 스쿨존)

>kids_accident.R

    library(ggplot2)
    library(dplyr)
    library(corrplot)
    # 데이터 불러오기
    df <-read.csv("kids_accident.csv", header=T, stringsAsFactors=F)
    # 데이터 변수 이름 변경 -- 한글 너무 길어서
    df <- rename(df, year='년도', kids_a='어린이_교통사고.건.', kids_d='어린이_사망.명.',zone_a='스쿨존_교통사고.건.', zone_d='스쿨존_사망.명.', cnt_zone='스쿨존_지정.곳.')
    df
    #어린이 사고vs 스쿨존 갯수 -- 정확히 보이는 부적 관계
    ggplot(data=df, aes(x=year, y=kids_a)) + 
    geom_line(color="blue") + 
    geom_line(aes(x=year,y=cnt_zone), color="red")
    df$kids_dx3 = df$kids_d * 3
    df
    #어린이 사망X3 vs 스쿨존 사고 -- 어린이 사망이 줄어드는데 비해 스쿨존 사고는 줄지X
    ggplot(data=df, aes(x=year, y=kids_dx3)) +
    geom_line(color="blue")+geom_line(aes(x=year,y=zone_a), color="red")
    df_c <- df[, c("kids_a","kids_d","zone_a","zone_d","cnt_zone")]
    df_c
    #상관분석 함수 적용
    df_cor <- cor(df_c)
    #히트맵 그래프
    col <- colorRampPalette(c("#BB4444","#EE9988","#FFFFFF","#77AADD","#4477AA"))
    corrplot(df_cor, method="color",col=col(200), type="lower",order="hclust",addCoef.col="black",diag=T)
    
>cj_zone_data.R

    library(ggplot2)
    library(dplyr)
    library(corrplot)
    library(readxl)
    library(stringr) # 문자열 처리를 위한 라이브러리
    ################################
    # cj_zone_data.R 설명
    # 이 스크립트는 청주 지역 스쿨존과 기타 교통안전 시설과의 상관도 분석, 시각화를 위해
    # 3가지 CSV 파일(기초데이터: 어린이보호구역(CCTV포함) + 스쿨존어린이교통사고 + 청주 신호등정보)을
    # 불러 들여 하나의 CSV 파일로 데이터를 정제, 전처리하는 프로그램이다.
    #################################
    
    #################################
    # 1. 데이터 불러오기
    #################################
    accident <-read.csv("12_19_schoolzone.csv", header=T, stringsAsFactors=F)
    zone_info <-read.csv("충청북도_청주시_어린이보호구역_20200717_1594961127925_45579.csv", header=T, stringsAsFactors=F)
    lamp_info <-read.csv("충청북도_청주시_신호등정보_20191007.csv", header=T, stringsAsFactors=F)
    
    #################################
    # 2. 데이터 정제
    #################################
    # 전국 스쿨존 사고 중 청주 데이터만 추출 "청주"가 들어있는 데이터만 추출
    accident <- accident[str_detect(accident$"시도시군구명",'청주'),]
    # 스쿨존 중복 정보 제거 (ex) 초등학교 부설 유치원
    # == 소재지지번주소가 같은 것을 중복으로 보고 하나만 남김
    zone_info2 = zone_info[-which(duplicated(zone_info$"소재지지번주소")), ] 
    # 특수학교 및 초등학교 단어 처리
    # == 초등학교, 초교 --> '초'로 변경 / (특수) 등의 문자를 없애줌 
    zone_info2$'대상시설명' <- str_replace(zone_info2$'대상시설명',"초등학교","초")
    zone_info2$'대상시설명' <- str_replace(zone_info2$'대상시설명',"초교","초")
    zone_info2$'대상시설명' <- str_replace(zone_info2$'대상시설명',"(특수)","")
    zone_info2$'대상시설명' <- str_replace(zone_info2$'대상시설명',"청주분원","")
    zone_info2$'대상시설명' <- str_replace(zone_info2$'대상시설명',"청주","")
    # 신호등 정보에 결측치 제거, ""으로 된 공백 데이터도 제거
    lamp_info <- lamp_info %>% filter(!is.na('교차로')) # 결측치 제거
    lamp_info <- lamp_info %>% filter(lamp_info$'교차로'!="") #공백 데이터도 제거
    #사고 데이터를 스쿨존 단위로 집계
    data_acc <- accident %>% group_by(지점명) %>% summarise(cnt_a = sum(발생건수),cnt_d = sum(사망자수))
    data_acc
    
    #################################
    # 3. 스쿨존 정보에 여러가지 컬럼 추가
    #    1) 신호등 컬럼 추가 (from 신호등 정보)
    #    2) 지역구 컬럼 추가 
    #    3) 사고 발생건수, 사망자 컬럼 추가 (from 어린이사고 정보)
    #################################
    # 1) 스쿨존 정보에 신호등 컬럼 추가
    # == for 문 사용하여 각 스쿨존에 해당하는 신호등(교차로) 정보가 있는지 확인하여
    # == 신호등(교차로) 정보가 있으면 'Y'을, 없으면 'N'을 값으로 스쿨존 정보에 넣음
    zones <- zone_info2$'대상시설명'
    lamp_info$'교차로'
    lamp <- c() # 신호등 정보 Y, N을 담을 벡터
    i <- 1  # 신호등 정보 벡터의 인덱스
    for (zone in zones){
      lamp[i] = ifelse(lamp_info %>% filter(str_detect(교차로, zone)) %>% nrow > 0, 'Y','N')
      i <- i+1
    }
    zone_info2$'신호등' <- lamp # 스쿨존 정보에 '신호등' 컬럼으로 설정
    zone_info2
    # 2) 스쿨존 정보에 지역구 컬럼 추가
    # == 스쿨존의 소재지도로명 주소에 있는 구을 바탕으로 지역구를 설정함
    zone_info2$'지역구' <- ifelse(str_detect(zone_info2$'소재지도로명주소','상당구'),'상당구',
                  ifelse(str_detect(zone_info2$'소재지도로명주소','서원구'),'서원구',
                  ifelse(str_detect(zone_info2$'소재지도로명주소','청원구'),'청원구',
                  ifelse(str_detect(zone_info2$'소재지도로명주소','흥덕구'),'흥덕구','기타'))))
    zone_info2$'지역구'
    # 3) 스쿨존 정보에 사고 발생건수, 사망자 컬럼 추가
    # == for문을 돌면서 해당스쿨존에 해당하는 사고의 발생건수, 사망자를 조사하여 컬럼 정보를 만든다
    # == for문을 돌면서 index 정보를 활용하여 새로운 컬럼과 기존의 스쿨존 정보의 인덱스를 맞춘다.
    areas <- zone_info2$'지역구'
    zones <- zone_info2$'대상시설명'
    i <- 1  # 벡터의 인덱스
    acci = c()
    dead = c()
    for (zone in zones){
      area = areas[i]
      row <- data_acc[str_detect(data_acc$지점명, zone) & str_detect(data_acc$지점명, area),]
      if(count(row)>0){
          acci[i] <- sum(row$cnt_a)
          dead[i] <- sum(row$cnt_d)
      }
      else{
           acci[i] <- 0
           dead[i] <- 0
      }
      # print(paste(zone,area,acci[i],dead[i]))
      i <- i+1
    }
    zone_info2$'발생건수' <- acci  
    # 스쿨존 정보에 '발생건수' 컬럼으로 설정
    zone_info2$'사망자수' <- dead  # 스쿨존 정보에 '사망자수' 컬럼으로 설정
    str(zone_info2)
    #################################
    # 4. 데이터 전처리가 끝난 스쿨존 정보를 CSV 파일로 저장한다.
    #################################
    write.csv(zone_info2, file="cj_schoolzone_Data2.csv")

>cj_zone_visual.R

    library(ggplot2)
    library(dplyr)
    library(corrplot)
    # 데이터 불러오기
    df <-read.csv("cj_schoolzone_Data2.csv", header=T, stringsAsFactors=F)
    # 필요한 데이터만 추출
    data = df[,c('지역구', '대상시설명', '신호등', 'CCTV설치여부', '발생건수', '사망자수')]
    data
    # 데이터 변수 이름 변경 -- 한글 너무 길어서
    data <- rename(data, gu='지역구', zone='대상시설명', lamp='신호등',cctv='CCTV설치여부', cnt_a='발생건수', cnt_d='사망자수')
    head(data)
    View(data)
    data
    data$lamp <- ifelse(data$lamp == "Y", 1, 0)
    data$cctv <- ifelse(data$cctv == "Y", 1, 0)
    data$zone <- ifelse(data$zone == "", 0, 1)
    data <- data[,c('gu','zone','lamp','cctv','cnt_a','cnt_d')]
    data_sum
    data_sum <- data %>%   
    group_by(gu) %>%   
    summarise(zone = sum(zone),
            lamp = sum(lamp),
            cctv = sum(cctv),
            cnt_a = sum(cnt_a),
            cnt_d = sum(cnt_d))
    #지역구별 스쿨존 갯수 (bar 그래프)
    ggplot(data=data_sum, aes(x=gu, y=zone))+geom_col()
    str(data_sum)
    dput(data_sum)
    #지역구별 데이터 (line 그래프)
    ggplot(data=data_sum, aes(x=gu, y=zone))+
      geom_line(color="blue", group = 1)+
        geom_line(aes(x=gu, y=lamp), color="red", group=2)+
          geom_line(aes(x=gu, y=cctv), color="yellow", group=3)+
            geom_line(aes(x=gu, y=cnt_a), color="orange", group=4)+
              geom_line(aes(x=gu, y=cnt_d), color="black", group=5)
              
    # 청주시 어린이 인구 수 추가 (단위 천명)
    data_sum$kids = c(21.40,20.14,26.67,32.34)
    data_sum
    # 어린이 인구 추가된 지역구별 데이터 (line 그래프)
    ggplot(data=data_sum, aes(x=gu, y=zone))+
      geom_line(color="blue", group = 1)+
        geom_line(aes(x=gu, y=lamp), color="red", group=2)+
          geom_line(aes(x=gu, y=cctv), color="yellow", group=3)+
            geom_line(aes(x=gu, y=cnt_a), color="orange", group=4)+
              geom_line(aes(x=gu, y=cnt_d), color="black", group=5)+
                geom_line(aes(x=gu, y=kids), color="green", group=6)
    data_sum$kids_r = round(data_sum$kids / data_sum$zone,3)
    data_sum$lamp_r = round(data_sum$lamp / data_sum$zone,3)
    data_sum$cctv_r = round(data_sum$cctv / data_sum$zone,3)
    data_sum$cnt_a_r = round(data_sum$cnt_a / data_sum$zone,3)
    data_sum$cnt_d_r = round(data_sum$cnt_d / ata_sum$zone,3)
    data_sum
    df <- data_sum[, c("kids_r","lamp_r","cctv_r","cnt_a_r")]
    df
    #상관분석 함수 적용
    df_cor <- cor(df)
    #히트맵 그래프
    col <- colorRampPalette(c("#BB4444","#EE9988","#FFFFFF","#77AADD","#4477AA"))
    corrplot(df_cor, method="color",col=col(200), type="lower",order="hclust",addCoef.col="black",diag=T)
    

<!--stackedit_data:
eyJoaXN0b3J5IjpbODQyNjg2MDU0LC0yMDI5NzE4NzUsNzY3NT
Q1ODc3LDIwODg0NjkzNTIsMTEwMDI2MDk1LDUwNTE1Mjc4MCwx
NTQ0NzYxNDg5LDIwMzI3NjgwMTMsNTI1NzE4MTkzLDMzMDU0Nj
k5MywtMTIxMDY1NjgyOSwtMTcyMTkxODAxMCwxNzU0ODAzNTIs
LTE4OTQ4NzcwODUsMTEyNTcxOTI5MSwzMjkwOTE2NTEsLTM0MT
I5NDMyMCwtNDcwMTU1NzY0LC0xODY1NzU1Mjc3LC0xNTkyMzgy
NjIzXX0=
-->
