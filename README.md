# fucking


Docker를 이용한 DOFBOT 환경 설정
Docker는 애플리케이션을 컨테이너로 배포하는 도구입니다. DOFBOT 컨트롤 소프트웨어를 Docker 컨테이너로 실행할 수 있습니다.

Docker 설정
=========================================
# Docker 설치
sudo apt-get update
sudo apt-get install -y docker.io

# Docker 실행
sudo systemctl start docker
sudo systemctl enable docker

# Docker 그룹에 사용자 추가
sudo usermod -aG docker $USER
Python 코드로 캘리브레이션 수행
python


============================================
from dofbot import DOFBOT
import time

# DOFBOT 인스턴스 생성
robot_arm = DOFBOT()

# 서보 모터 제어 함수
def set_servo_angle(channel, angle):
    robot_arm.Arm_PWM_servo_write(channel, angle)
    time.sleep(0.5)

# 로봇 팔 초기화 및 캘리브레이션
def calibrate_robot():
    initial_positions = [90, 90, 90, 90, 90, 90]  # 초기 위치 설정
    for channel in range(6):
        set_servo_angle(channel + 1, initial_positions[channel])
    print("Calibration complete. Initial positions set.")

# 메인 함수
def main():
    calibrate_robot()

if __name__ == "__main__":
    main()
