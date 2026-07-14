pipeline {
    agent any

    tools {
        // Khai báo công cụ sử dụng (Tên phải khớp chính xác với cấu hình trong Jenkins)
        jdk 'JDK 11'
        maven 'Maven 3'
    }

    stages {
        stage('Checkout') {
            steps {
                echo '--- ĐANG TẢI MÃ NGUỒN TỪ GITHUB ---'
                checkout scm
            }
        }

        stage('Compile Code') {
            steps {
                echo '--- ĐANG BIÊN DỊCH MÃ NGUỒN ---'
                sh 'mvn clean compile'
            }
        }

        stage('Run Unit Tests') {
            steps {
                echo '--- ĐANG CHẠY CÁC BÀI KIỂM TRA (UNIT TESTS) ---'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo '--- ĐANG ĐÓNG GÓI THÀNH FILE JAR ---'
                sh 'mvn package -DskipTests'
            }
        }
    }

    post {
        success {
            echo '=== PIPELINE HOÀN THÀNH XUẤT SẮC! ==='
        }
        failure {
            echo '=== PIPELINE THẤT BẠI! VUI LÒNG KIỂM TRA LẠI CODE HOẶC CẤU HÌNH ==='
        }
    }
}





