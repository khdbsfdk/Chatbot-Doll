# 기업 연계 프로젝트 - 안드로이드 앱을 이용한 챗봇
- 작업 인원 1명
---
# 차례
- [프로젝트 개요](https://github.com/khdbsfdk/Chatbot-Doll/blob/main/README.md#%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EA%B0%9C%EC%9A%94)
- [프로젝트 수행 절차](https://github.com/khdbsfdk/Chatbot-Doll/blob/main/README.md#%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%88%98%ED%96%89-%EC%A0%88%EC%B0%A8---%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C)
  - [안드로이드](https://github.com/khdbsfdk/Chatbot-Doll/blob/main/README.md#%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%88%98%ED%96%89-%EC%A0%88%EC%B0%A8---%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C)
  - [챗봇](https://github.com/khdbsfdk/Travel-recommendation-AI/blob/main/README.md#%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%88%98%ED%96%89-%EC%A0%88%EC%B0%A8---%EC%B1%97%EB%B4%87)
  - [데이터 베이스](https://github.com/khdbsfdk/Travel-recommendation-AI/blob/main/README.md#%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%88%98%ED%96%89-%EC%A0%88%EC%B0%A8---%EC%B6%94%EC%B2%9C-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98)
- [참고 사이트](https://github.com/khdbsfdk/Travel-recommendation-AI/blob/main/README.md#%EC%B6%9C%EC%B2%98-%EB%B0%8F-%EC%B0%B8%EA%B3%A0-%EC%82%AC%EC%9D%B4%ED%8A%B8)
---
# 프로젝트 개요
### (1)프로젝트 구현 내용
- 플랫폼 -> 안드로이드 앱 구현
- 챗봇 -> 자연어 처리
### (2)프로젝트 의의
- 컴퓨터 이외의 환경에서 챗봇을 사용할 수 있습니다.
- 안드로이드 앱과 데이터 베이스 설계 능력 또한 키울 수 있습니다.
### (3)개발 환경
- 코랩 or 주피터 노트북
- 안드로이드 스튜디오 ide-201.6953283-windows
- 파이어 베이스(DB)
### (4)기대 효과
- 앱 설치로 인해 접근성이 쉬우며, 채팅이 아닌 음성으로 대화를 하기 때문에 손이 자유롭습니다.
- 독거 노인분들을 위한 챗봇도 가능해 보입니다.
---
## 프로젝트 수행 절차 - 안드로이드
- 안드로이드 스튜디오를 사용하여 앱을 구현했습니다. STT와 TTS 모두를 사용하며, 버튼 하나로 작동합니다.
- activity_main.xml 코드
``` android
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".MainActivity">

<TextView
    android:id="@+id/textView3"
    android:layout_width="0dp"
    android:layout_height="wrap_content"
    android:layout_marginTop="16dp"
    android:gravity="center"
    android:text="챗봇 인형"
    android:textColor="@color/black"
    android:textSize="30dp"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.0"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    tools:ignore="MissingConstraints" />

<Button
    android:id="@+id/btn_stt_start"
    android:layout_width="206dp"
    android:layout_height="59dp"
    android:backgroundTint="#0780E1"
    android:text="음성 인식"
    android:textSize="20dp"
    app:icon="@drawable/mic"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.497"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    app:layout_constraintVertical_bias="0.558" />

<EditText
    android:id="@+id/editText"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="100dp"
    android:text="Press mic button to input voice..."
    android:textColor="@color/black"
    android:textSize="20dp"
    app:layout_constraintBottom_toTopOf="@+id/tv_answer"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.495"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="@+id/textView3"
    app:layout_constraintVertical_bias="0.17" />

<TextView
    android:id="@+id/tv_answer"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginTop="236dp"
    android:text="답변"
    android:textColor="@color/black"
    android:textSize="20dp"
    app:layout_constraintBottom_toTopOf="@+id/btn_stt_start"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintHorizontal_bias="0.498"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    app:layout_constraintVertical_bias="0.25" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
- MainActivity.java 코드
``` android
import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;

import android.Manifest;
import static android.speech.tts.TextToSpeech.ERROR;
import android.content.Intent;
import android.os.Build;
import android.os.Bundle;
import android.os.Handler;
import android.speech.RecognitionListener;
import android.speech.RecognizerIntent;
import android.speech.SpeechRecognizer;
import android.speech.tts.TextToSpeech;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import com.google.firebase.database.ChildEventListener;
import com.google.firebase.database.DataSnapshot;
import com.google.firebase.database.DatabaseError;
import com.google.firebase.database.DatabaseReference;
import com.google.firebase.database.FirebaseDatabase;
import com.google.firebase.database.ValueEventListener;

import java.util.ArrayList;
import java.util.Locale;

public class MainActivity extends AppCompatActivity {

    Intent intent;
    String text_to_speak;
    final int PERMISSION = 1;
    private TextToSpeech tts;
    SpeechRecognizer mRecognizer;

    private Button btn_stt_start;
    private TextView tv_answer;
    private EditText editText;

    private FirebaseDatabase mDatabase;
    private ChildEventListener mChild;
    private DatabaseReference mReference, testReference;
    public String msg;
    Handler handler = new Handler();
    int i;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // 데이터 베이스 감시
        initDatabase();

        btn_stt_start = findViewById(R.id.btn_stt_start);
        editText = findViewById(R.id.editText);
        tv_answer = findViewById(R.id.tv_answer);

        // 안드로이드 6.0버전 이상인지 체크해서 퍼미션 체크
        if(Build.VERSION.SDK_INT >= 23){
            ActivityCompat.requestPermissions(this, new String[] {Manifest.permission.INTERNET,
                    Manifest.permission.RECORD_AUDIO},PERMISSION);
        }

        // RecognizerIntent 생성
        intent = new Intent(RecognizerIntent.ACTION_RECOGNIZE_SPEECH);
        intent.putExtra(RecognizerIntent.EXTRA_CALLING_PACKAGE,getPackageName()); // 여분의 키
        intent.putExtra(RecognizerIntent.EXTRA_LANGUAGE,"ko-KR"); // 언어 설정

        // 버튼 클릭 시 객체에 Context와 listener를 할당
        btn_stt_start.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // 음성 -> 텍스트 변환
                mRecognizer = SpeechRecognizer.createSpeechRecognizer(MainActivity.this); // 새 SpeechRecognizer 를 만드는 팩토리 메서드
                mRecognizer.setRecognitionListener(listener); // 리스너 설정
                mRecognizer.startListening(intent); // 듣기 시작
            }
        });

    }

    private RecognitionListener listener = new RecognitionListener() {
        @Override
        public void onReadyForSpeech(Bundle params) {
            // 말하기 시작할 준비가되면 호출
            Toast.makeText(getApplicationContext(),"음성인식 시작",Toast.LENGTH_SHORT).show();
        }

        @Override
        public void onBeginningOfSpeech() {
            // 말하기 시작했을 때 호출
        }

        @Override
        public void onRmsChanged(float rmsdB) {
            // 입력받는 소리의 크기를 알려줌
        }

        @Override
        public void onBufferReceived(byte[] buffer) {
            // 말을 시작하고 인식이 된 단어를 buffer에 담음
        }

        @Override
        public void onEndOfSpeech() {
            // 말하기를 중지하면 호출
        }

        @Override
        public void onError(int error) {
            // 네트워크 또는 인식 오류가 발생했을 때 호출
            String message;

            switch (error) {
                case SpeechRecognizer.ERROR_AUDIO:
                    message = "오디오 에러";
                    break;
                case SpeechRecognizer.ERROR_CLIENT:
                    message = "클라이언트 에러";
                    break;
                case SpeechRecognizer.ERROR_INSUFFICIENT_PERMISSIONS:
                    message = "퍼미션 없음";
                    break;
                case SpeechRecognizer.ERROR_NETWORK:
                    message = "네트워크 에러";
                    break;
                case SpeechRecognizer.ERROR_NETWORK_TIMEOUT:
                    message = "네트웍 타임아웃";
                    break;
                case SpeechRecognizer.ERROR_NO_MATCH:
                    message = "찾을 수 없음";
                    break;
                case SpeechRecognizer.ERROR_RECOGNIZER_BUSY:
                    message = "RECOGNIZER 가 바쁨";
                    break;
                case SpeechRecognizer.ERROR_SERVER:
                    message = "서버가 이상함";
                    break;
                case SpeechRecognizer.ERROR_SPEECH_TIMEOUT:
                    message = "말하는 시간초과";
                    break;
                default:
                    message = "알 수 없는 오류";
                    break;
            }

            Toast.makeText(getApplicationContext(), "에러 발생 : " + message,Toast.LENGTH_SHORT).show();
        }
        // 음성 인식 후 처리 함수
        @Override
        public void onResults(Bundle results) {
            // 인식 결과가 준비되면 호출
            // 말을 하면 ArrayList에 단어를 넣고 textView에 단어를 이어줌
            ArrayList<String> matches =
                    results.getStringArrayList(SpeechRecognizer.RESULTS_RECOGNITION);

            for(int i = 0; i < matches.size() ; i++){
                editText.setText(matches.get(i));
            }
            msg = editText.getText().toString();
            mReference.child("question").setValue(msg);

            testReference = mDatabase.getReference("state"); // test
            testReference.child("log").setValue("chek");

            // 딜레이
            new Handler().postDelayed(new Runnable() {
                @Override
                public void run() {
                    // 데이터 불러오기
                    mReference = mDatabase.getReference("log"); // 변경값을 확인할 child 이름

                    mReference.addListenerForSingleValueEvent(new ValueEventListener() {
                        @Override
                        public void onDataChange(@NonNull DataSnapshot dataSnapshot) {

                            for (DataSnapshot messageData : dataSnapshot.getChildren()) {
                                // child 내에 있는 데이터만큼 반복해서 변화한 데이터 찾기
                                String msg2 = messageData.getValue().toString();
                                tv_answer.setText(msg2);
                            }
                            // 다 끝나면 음성으로 출력
                            speak(tv_answer.getText().toString());
                        }

                        @Override
                        public void onCancelled(@NonNull DatabaseError error) {

                        }
                    });
                    //딜레이 후 시작할 코드 작성
                }
            }, 1500);// 1.5초 정도 딜레이

        }

        @Override
        public void onPartialResults(Bundle partialResults) {
            // 부분 인식 결과를 사용할 수 있을 때 호출
        }

        @Override
        public void onEvent(int eventType, Bundle params) {
            // 향후 이벤트를 추가하기 위해 예약
        }
    };
    // 음성 출력 함수
    private void speak(String text) {
        tts = new TextToSpeech(getApplicationContext(), new TextToSpeech.OnInitListener() {
            @Override
            public void onInit(int status) {
                if (status != ERROR) {
                    int result = tts.setLanguage(Locale.KOREA); // 언어 선택
                    if (result == TextToSpeech.LANG_NOT_SUPPORTED || result == TextToSpeech.LANG_MISSING_DATA) {
                        Log.e("TTS", "This Language is not supported");
                    } else {
                        tts.speak(text, TextToSpeech.QUEUE_FLUSH, null, null);
                    }
                } else {
                    Log.e("TTS", "Initialization Failed!");
                }
            }
        });
    }
    @Override
    protected void onDestroy() {
        super.onDestroy();
        if(tts!=null){ // 사용한 TTS객체 제거
            tts.stop();
            tts.shutdown();
        }
        super.onDestroy();
        mReference.removeEventListener(mChild);
    }
    // 데이터 변화 감지 함수들
    private void initDatabase() {

        mDatabase = FirebaseDatabase.getInstance();

        mReference = mDatabase.getReference("log");
        mReference.child("log").setValue("check");

        mChild = new ChildEventListener() {

            @Override
            public void onChildAdded(DataSnapshot dataSnapshot, String s) {

            }

            @Override
            public void onChildChanged(DataSnapshot dataSnapshot, String s) {

            }

            @Override
            public void onChildRemoved(DataSnapshot dataSnapshot) {

            }

            @Override
            public void onChildMoved(DataSnapshot dataSnapshot, String s) {
            }

            @Override
            public void onCancelled(DatabaseError databaseError) {

            }
        };
        mReference.addChildEventListener(mChild);
    }


}
```

# 프로젝트 수행 절차 - 챗봇
### (1) 챗봇을 사용한 이유
- 음성을 통한 대화용 챗봇을 만들고자 했습니다.
- 음성을 변환한 문장을 받아 챗봇이 답변하고, 다시 음성으로 바꾸어 사용자와 대화하게 구현했습니다.
### (2) 챗봇의 종류
- 본 프로젝트는 **일상 대화**에 중점을 두었고, 대화용 챗봇을 목적으로 합니다.
- 추가로 음성으로 대화하는 챗봇입니다.
### (3) 챗봇 데이터
- 챗봇 데이터를 송영숙님 데이터에서 가져왔습니다.
- https://github.com/songys/Chatbot_data

### (4) 챗봇 학습 진행
- 제가 사용한 모델은 transformers의 bert입니다.

- 저장한 챗봇 데이터 프레임에 임베딩 값을 구한 후 코사인 유사도를 구합니다.
<img width="100%" src="https://user-images.githubusercontent.com/84302953/168531538-f7e8360a-67f3-4ee5-93fb-feca2cfdb0d9.png"/>

- 질문 문장을 넣으면 데이터 프레임 중 가장 유사한 질문 문장을 찾아 답변합니다.
<img width="80%" src="https://user-images.githubusercontent.com/84302953/168531771-3e8a6037-1623-4bdd-b616-4444064d7c7d.png"/>

## 프로젝트 수행 절차 - 파이어 베이스
#### (1) 안드로이드와 연동
- 안드로이드에서 지원하는 데이터 베이스인 파이어 베이스를 이용했습니다.
- 연동 시 파이어 베이스에서 제공하는 자료와 안드로이드 스튜디오의 내부 코드가 달라 고생했습니다.
- 특히 안드로이드 스튜디오의 버전이 높으면 연동이 불가합니다. 따라서 버전을 20년도 버전으로 바꿔서 진행했습니다.
#### (2) 파이썬과 연동
- 파이어 베이스와 연결하기 위해 라이브러리를 설치해줍니다.
``` python
pip3 install firebase_admin
```
``` python
import firebase_admin
from firebase_admin import credentials
from firebase_admin import db
 
 #Firebase database 인증 및 앱 초기화
cred = credentials.Certificate('chat-db.json')
firebase_admin.initialize_app(cred,{
    'databaseURL' : 'https://chat-db-32cde-default-rtdb.firebaseio.com/'
})
```
- 파이어 베이스에서 데이터를 읽고 쓰는 방법입니다.
``` python
# 데이터 읽기
dir2 = db.reference('state/log')
print(dir2.get())
# 데이터 쓰기
dir = db.reference('log')
dir.update({'log':'None'})
dir.update({'question':result_text})
```
- 이제 반복문을 사용하여 안드로이드에서 데이터를 저장하면 챗봇이 답변하게 만들어줍니다.
``` python
while 1:
    #계속 데이터 읽기
    ref = db.reference('log/question')
    ref2 = db.reference('state/log')
    dir = db.reference('log')
    dir2 = db.reference('state')

    #ref.get()는 #json형태로 받아옴
    if ref.get() == 'stop':
        break
    # 무한 반복 중에서도 원할 때만 값 변경 하기
    elif ref2.get() != "None":
        score, result_text, label = return_answer(ref.get())

        if score >= 30:
            print(result_text)
            print("score : ", score)
            dir.update({'question':result_text})
            dir2.update({'log':'None'})
        else:
            print("잘 못 알아들었어요.")
            dir2.update({'log':'None'})
```
- 따라서 크롤링 시 명소 이름, 주소, 테마를 저장합니다.
<img width="100%" src="https://user-images.githubusercontent.com/84302953/165223874-3300f74a-3b2c-4ecc-b71e-af272a61012c.png"/>

#### (3) 데이터 정제
- 비슷한 의미의 태그는 묶어서 하나의 테마로 만듭니다.
- 예를들어 "아이"와 "어린이"는 '어린이'라는 하나의 단어로 묶습니다.
<img width="100%" src="https://user-images.githubusercontent.com/84302953/165226576-751c3a16-d253-4118-9fc2-929182fa84f3.png"/>

- 이후 테마에 해당하는 태그의 개수를 세어 데이터 프레임을 만듭니다.
<img width="80%" src="https://user-images.githubusercontent.com/84302953/165227200-9c784d85-7678-4980-a968-249363d87075.png"/>

#### (4) [모델 선정(ALS: Alternating Least Squares)](https://yeomko.tistory.com/8?category=805638)
- 추천 알고리즘으로 ALS를 선택했습니다.
- **ALS 알고리즘** : 행렬 분해를 최적화하는 잠재 요인의 유저 협업 필터링 기반의 추천 알고리즘으로서, loss function이 최소가 되는 행렬 x, y를 추출하는데 목적을 가진 알고리즘.
- ALS 알고리즘을 **선택한 이유** : 사용자가 선택하지 않은 테마에 대해서 유의미한 영향을 끼치지 않는다라고 판단하는 것은 옳지 않다고 생각했습니다. 따라서 선택하지 않은 태그, 잠재 요인도 고려하여 사용자가 선택한 테마에 가장 적합한 장소를 추천하기 위해 선정하게 되었습니다.

#### (5) 알고리즘 수행
- 입력 데이터 + 학습 데이터 ALS 행렬 연산 수행
- 입력 데이터와 학습 데이터 간의 코사인 유사도 연산 수행
- 코사인 유사도를 기준으로 상위 10개의 데이터(행 인덱스 번호, 행렬) 추출
- 입력 데이터와의 태그 부합 개수를 기준으로 랭크 정렬
- 상위 n 개의 관광지 명과 상세 주소 출력
<img width="60%" src="https://user-images.githubusercontent.com/84302953/165258890-c627432a-a253-4730-bf7c-eb80856bebb0.png"/>

## 개선 할 사항
- 챗봇 및 지도 그림을 이용한 여행지 시각화 웹 페이지 구현
- 추천 알고리즘 속도 개선
- 더욱 다양한 대화가 가능한 챗봇, 실시간 날씨 정보 표시

## 출처 및 참고 사이트
- 챗봇 -> [송영숙님 깃허브](https://github.com/songys/Chatbot_data), [BERT의 문장 임베딩(SBERT)을 이용한 한국어 챗봇](https://wikidocs.net/154530)
- 안드로이드와 파이어 베이스 연동 -> [real-time database](https://soopeach.tistory.com/78)
- 안드로이드 음성 변환 -> [STT](https://hanyeop.tistory.com/128)
