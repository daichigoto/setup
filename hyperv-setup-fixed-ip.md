# Hyper-V ゲスト環境を固定IPで使うセットアップ

1. Hyper-Vマネージャー：「操作」→「仮想スイッチマネージャー」
2. 仮想スイッチマネージャー：「内部」→「仮想スイッチの作成」→「名前」に認識やすい名前を入力→「OK」
3. 設定アプリケーション：「ネットワーク」→「状態」→「アダプターのオプションを変更する」
4. ネットワーク接続：作成した仮想スイッチ（vEthernet）を選択→「プロパティ」→「インターネットプロトコルバージョン4 (TCP/IPv4)」→「プロパティ」

##### 設定内容

    次のIPアドレスを使う
        IPアドレス:           192.168.185.1
        サブネットマスク:     255.255.255.0

5. Hyper-Vマネージャー：仮想マシンを選択→「設定…」→「ネットワークアダプター」→「仮想スイッチ」→作成した仮想スイッチを選択→「OK」
6. 仮想マシンを起動し、ゲストOSで固定IPを設定

##### 設定内容

    デフォルトゲートウェイ:   192.168.185.1
    IPアドレス:               192.168.185.50
    サブネットマスク:         255.255.255.0
    DNSサーバ:                8.8.8.8

7. 管理者権限のWindows Terminal：

##### 実行するコマンド

    PS C:\Users\daichi> New-NetNat -Name "192.168.185.0/24" -InternalIPInterfaceAddressPrefix 192.168.185.0/24
    
    Name                             : 192.168.185.0/24
    ExternalIPInterfaceAddressPrefix :
    InternalIPInterfaceAddressPrefix : 192.168.185.0/24
    IcmpQueryTimeout                 : 30
    TcpEstablishedConnectionTimeout  : 1800
    TcpTransientConnectionTimeout    : 120
    TcpFilteringBehavior             : AddressDependentFiltering
    UdpFilteringBehavior             : AddressDependentFiltering
    UdpIdleSessionTimeout            : 120
    UdpInboundRefresh                : False
    Store                            : Local
    Active                           : True
    
    
    PS C:\Users\daichi>
