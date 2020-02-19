# 데이터 통신공학 Summary 

<br/>
3학년 2학기 수업 때 수강한 데이터 통신 공학 코스 내용을 간단히 정리했습니다.


## 1. Network Models
 
- TCP , IP 
- OSI models
    <center><img src = 'https://miro.medium.com/max/674/1*Mmwq193cCMdRelBIqtN0ew.png' style = "width: 600px; height: auto;" > </center>

## 2. Intro to Physical Layer

- Data & Signal<br/>

- Analogue & Digital<br/>

- Periodic Analog Signals <br/>

    - Periods, Frequency, Phases.. 
    - Simple Analogue Signals & Composite Analogue Signals <br/>

- **Nonperiodic Digital Signals**
    <br/>
    
    1) Bit Rate

    2) Two ways to transmit the Digital Signals : Baseband & Broadband


        1) **Baseband transmission**
            - two cases 
                1. wide bandwidth
                    - Transmission Available without any converison 
                2. limited bandwidth 
                    - Lowpass channel (Approximate to Analogue)


        2) **Broadband Transmission** 
            - Bandpass
            - Modulation 
                - Digital Signal -> (Carrier) -> Composite Analogue Signal -> Digital signal 


    <center><img src = 'https://www.norwegiancreations.com/wp-content/uploads/2016/03/filters.png' style="width=600px; height = auto;">  *Lowpass and Bandpass*
    </center>

    <br/>
    
    4) Transmission Impairment 
        -  dB
        - SNR
        - SNRdB

    5) Data Rate Limit
        - Nyquist Bitrate 
        - Bitrate with noises 


## 3. Digital Transmission
    
-   **Digital(Data) to Digital(Signal) Conversion**

    *How Can We Represent DIGITAL DATA with DIGITAL SIGNAL?*
    - Line Coding
        <center><img src = 'https://t1.daumcdn.net/cfile/tistory/9964C63B5CB31DB410'>
        </center>
        
        1.  Examples : NRZ, RZ, Manchester etc

        2. Problems
            - Baseline Wandering
            - DC components
            - Synchronization
            
    <br/>

    - Block Coding

    

- **Analogue(Signal) to Digital(Data) Conversion**

    - PCM 
        - Sampling Analogue Signal

- Transmission : Paralell or Serial


## 4. Analogue Transmission

- Digital Data to Analogue Signal<br/>
<br/>(When *Bandpass* Channel is Available!) 


- Broadband modulation 
    - ASK, FSK, QAM etc
    <center><img src = 'https://www.analog.com/-/media/images/analog-dialogue/en/volume-46/number-1/articles/fsk-psk-modulator-uses-multichannel-dds/ad46-01_bb_fig_01.jpg?la=en' ></center>

- Analogue Signal (low pass) to Smaller Analogue Signal(band pass) 
    - AM, FM etc


## 5. In Real Life, Usually It's Limited Bandwidth :-( 

- Solution : Several Low Bandwidth Channels into One Channel with Large Bandwith

    - Multiplexing 
        1. For Efficiency
        2. Multiple Signals across single link
        3. Example : WDM, FDM, TDM

    - Spectrum Spreading
        1. For Privacy and Anti-jamming
        2. FHSS
        3. DSSS - Spreading Code 



## 6. Switching
- Circuit
    - Physical Layer (Resource Reservation)
- Packet
    - Datagram(Routing table) : Network Layer
    - Virtual- Circuit (Switching Table): Data-Link Layer 
    
    <center><img src = 'https://www.myreadingroom.co.in/images/stories/docs/dcn/Virtual%20Circuit%20Network_Data%20Transfer%20setup.JPG'><br/>
    *Virtual Circuit*
    </center>

- Message


## 7. Data Link Layer 


- DLC 
    - Framing
- Multiple Access Resolution
    - Random Access (Data Link Layer)
        - ALOHA, CSMA, CSMA/CA, CSMA/CD
    <center><img src = 'https://images.slideplayer.com/39/10835838/slides/slide_2.jpg' style = "width:600px; height: auto;">
