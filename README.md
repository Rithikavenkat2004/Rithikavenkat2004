{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": []
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "source": [
        "# **[YBI Foundation](https://www.ybifoundation.org/)**"
      ],
      "metadata": {
        "id": "eSJhECflLke8"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "**[Join Telegram to Get Updates of all Future FREE Bootcamps and Courses](https://telegram.me/ybif_ybifoundation)**"
      ],
      "metadata": {
        "id": "k6j_cKG6Lke8"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "# **Binary Classification**"
      ],
      "metadata": {
        "id": "KX9SMfuULke8"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "**[Watch Video Tutorial](https://www.youtube.com/c/YBIFoundation?sub_confirmation=1)**"
      ],
      "metadata": {
        "id": "CZ1cpxYRLke8"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Step 1 : import library\n",
        "import pandas as pd"
      ],
      "metadata": {
        "id": "EgbkrIwhLke8"
      },
      "execution_count": 1,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# Step 2 : import data\n",
        "diabetes = pd.read_csv('https://github.com/YBIFoundation/Dataset/raw/main/Diabetes.csv')"
      ],
      "metadata": {
        "id": "D6BtrmedLke9"
      },
      "execution_count": 2,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "diabetes.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 206
        },
        "id": "OB0Xga8QMBmk",
        "outputId": "de7c97d5-02ba-4acc-da94-5e6027e39436"
      },
      "execution_count": 3,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "   pregnancies  glucose  diastolic  triceps  insulin   bmi    dpf  age  \\\n",
              "0            6      148         72       35        0  33.6  0.627   50   \n",
              "1            1       85         66       29        0  26.6  0.351   31   \n",
              "2            8      183         64        0        0  23.3  0.672   32   \n",
              "3            1       89         66       23       94  28.1  0.167   21   \n",
              "4            0      137         40       35      168  43.1  2.288   33   \n",
              "\n",
              "   diabetes  \n",
              "0         1  \n",
              "1         0  \n",
              "2         1  \n",
              "3         0  \n",
              "4         1  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-ec8b419d-ad15-4e90-afb4-2971643f1958\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>pregnancies</th>\n",
              "      <th>glucose</th>\n",
              "      <th>diastolic</th>\n",
              "      <th>triceps</th>\n",
              "      <th>insulin</th>\n",
              "      <th>bmi</th>\n",
              "      <th>dpf</th>\n",
              "      <th>age</th>\n",
              "      <th>diabetes</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>6</td>\n",
              "      <td>148</td>\n",
              "      <td>72</td>\n",
              "      <td>35</td>\n",
              "      <td>0</td>\n",
              "      <td>33.6</td>\n",
              "      <td>0.627</td>\n",
              "      <td>50</td>\n",
              "      <td>1</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>1</td>\n",
              "      <td>85</td>\n",
              "      <td>66</td>\n",
              "      <td>29</td>\n",
              "      <td>0</td>\n",
              "      <td>26.6</td>\n",
              "      <td>0.351</td>\n",
              "      <td>31</td>\n",
              "      <td>0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>8</td>\n",
              "      <td>183</td>\n",
              "      <td>64</td>\n",
              "      <td>0</td>\n",
              "      <td>0</td>\n",
              "      <td>23.3</td>\n",
              "      <td>0.672</td>\n",
              "      <td>32</td>\n",
              "      <td>1</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>1</td>\n",
              "      <td>89</td>\n",
              "      <td>66</td>\n",
              "      <td>23</td>\n",
              "      <td>94</td>\n",
              "      <td>28.1</td>\n",
              "      <td>0.167</td>\n",
              "      <td>21</td>\n",
              "      <td>0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>0</td>\n",
              "      <td>137</td>\n",
              "      <td>40</td>\n",
              "      <td>35</td>\n",
              "      <td>168</td>\n",
              "      <td>43.1</td>\n",
              "      <td>2.288</td>\n",
              "      <td>33</td>\n",
              "      <td>1</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-ec8b419d-ad15-4e90-afb4-2971643f1958')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "       width=\"24px\">\n",
              "    <path d=\"M0 0h24v24H0V0z\" fill=\"none\"/>\n",
              "    <path d=\"M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z\"/><path d=\"M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z\"/>\n",
              "  </svg>\n",
              "      </button>\n",
              "      \n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      flex-wrap:wrap;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "      <script>\n",
              "        const buttonEl =\n",
              "          document.querySelector('#df-ec8b419d-ad15-4e90-afb4-2971643f1958 button.colab-df-convert');\n",
              "        buttonEl.style.display =\n",
              "          google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "        async function convertToInteractive(key) {\n",
              "          const element = document.querySelector('#df-ec8b419d-ad15-4e90-afb4-2971643f1958');\n",
              "          const dataTable =\n",
              "            await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                     [key], {});\n",
              "          if (!dataTable) return;\n",
              "\n",
              "          const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "            '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "            + ' to learn more about interactive tables.';\n",
              "          element.innerHTML = '';\n",
              "          dataTable['output_type'] = 'display_data';\n",
              "          await google.colab.output.renderOutput(dataTable, element);\n",
              "          const docLink = document.createElement('div');\n",
              "          docLink.innerHTML = docLinkHtml;\n",
              "          element.appendChild(docLink);\n",
              "        }\n",
              "      </script>\n",
              "    </div>\n",
              "  </div>\n",
              "  "
            ]
          },
          "metadata": {},
          "execution_count": 3
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "diabetes.info()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "CBAyTJZsMBtm",
        "outputId": "f90889cb-d6e9-44c4-a5e1-69791cfdf1a9"
      },
      "execution_count": 4,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'pandas.core.frame.DataFrame'>\n",
            "RangeIndex: 768 entries, 0 to 767\n",
            "Data columns (total 9 columns):\n",
            " #   Column       Non-Null Count  Dtype  \n",
            "---  ------       --------------  -----  \n",
            " 0   pregnancies  768 non-null    int64  \n",
            " 1   glucose      768 non-null    int64  \n",
            " 2   diastolic    768 non-null    int64  \n",
            " 3   triceps      768 non-null    int64  \n",
            " 4   insulin      768 non-null    int64  \n",
            " 5   bmi          768 non-null    float64\n",
            " 6   dpf          768 non-null    float64\n",
            " 7   age          768 non-null    int64  \n",
            " 8   diabetes     768 non-null    int64  \n",
            "dtypes: float64(2), int64(7)\n",
            "memory usage: 54.1 KB\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "diabetes.describe()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 300
        },
        "id": "4_ImqgqAMB1i",
        "outputId": "f4663b1c-d176-4d28-8396-5772669ea3ca"
      },
      "execution_count": 5,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "       pregnancies     glucose   diastolic     triceps     insulin  \\\n",
              "count   768.000000  768.000000  768.000000  768.000000  768.000000   \n",
              "mean      3.845052  120.894531   69.105469   20.536458   79.799479   \n",
              "std       3.369578   31.972618   19.355807   15.952218  115.244002   \n",
              "min       0.000000    0.000000    0.000000    0.000000    0.000000   \n",
              "25%       1.000000   99.000000   62.000000    0.000000    0.000000   \n",
              "50%       3.000000  117.000000   72.000000   23.000000   30.500000   \n",
              "75%       6.000000  140.250000   80.000000   32.000000  127.250000   \n",
              "max      17.000000  199.000000  122.000000   99.000000  846.000000   \n",
              "\n",
              "              bmi         dpf         age    diabetes  \n",
              "count  768.000000  768.000000  768.000000  768.000000  \n",
              "mean    31.992578    0.471876   33.240885    0.348958  \n",
              "std      7.884160    0.331329   11.760232    0.476951  \n",
              "min      0.000000    0.078000   21.000000    0.000000  \n",
              "25%     27.300000    0.243750   24.000000    0.000000  \n",
              "50%     32.000000    0.372500   29.000000    0.000000  \n",
              "75%     36.600000    0.626250   41.000000    1.000000  \n",
              "max     67.100000    2.420000   81.000000    1.000000  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-afe7305f-f4cd-43f2-a8dd-c592dc3f5e5b\">\n",
              "    <div class=\"colab-df-container\">\n",
              "      <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>pregnancies</th>\n",
              "      <th>glucose</th>\n",
              "      <th>diastolic</th>\n",
              "      <th>triceps</th>\n",
              "      <th>insulin</th>\n",
              "      <th>bmi</th>\n",
              "      <th>dpf</th>\n",
              "      <th>age</th>\n",
              "      <th>diabetes</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>count</th>\n",
              "      <td>768.000000</td>\n",
              "      <td>768.000000</td>\n",
              "      <td>768.000000</td>\n",
              "      <td>768.000000</td>\n",
              "      <td>768.000000</td>\n",
              "      <td>768.000000</td>\n",
              "      <td>768.000000</td>\n",
              "      <td>768.000000</td>\n",
              "      <td>768.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>mean</th>\n",
              "      <td>3.845052</td>\n",
              "      <td>120.894531</td>\n",
              "      <td>69.105469</td>\n",
              "      <td>20.536458</td>\n",
              "      <td>79.799479</td>\n",
              "      <td>31.992578</td>\n",
              "      <td>0.471876</td>\n",
              "      <td>33.240885</td>\n",
              "      <td>0.348958</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>std</th>\n",
              "      <td>3.369578</td>\n",
              "      <td>31.972618</td>\n",
              "      <td>19.355807</td>\n",
              "      <td>15.952218</td>\n",
              "      <td>115.244002</td>\n",
              "      <td>7.884160</td>\n",
              "      <td>0.331329</td>\n",
              "      <td>11.760232</td>\n",
              "      <td>0.476951</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>min</th>\n",
              "      <td>0.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>0.078000</td>\n",
              "      <td>21.000000</td>\n",
              "      <td>0.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>25%</th>\n",
              "      <td>1.000000</td>\n",
              "      <td>99.000000</td>\n",
              "      <td>62.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>0.000000</td>\n",
              "      <td>27.300000</td>\n",
              "      <td>0.243750</td>\n",
              "      <td>24.000000</td>\n",
              "      <td>0.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>50%</th>\n",
              "      <td>3.000000</td>\n",
              "      <td>117.000000</td>\n",
              "      <td>72.000000</td>\n",
              "      <td>23.000000</td>\n",
              "      <td>30.500000</td>\n",
              "      <td>32.000000</td>\n",
              "      <td>0.372500</td>\n",
              "      <td>29.000000</td>\n",
              "      <td>0.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>75%</th>\n",
              "      <td>6.000000</td>\n",
              "      <td>140.250000</td>\n",
              "      <td>80.000000</td>\n",
              "      <td>32.000000</td>\n",
              "      <td>127.250000</td>\n",
              "      <td>36.600000</td>\n",
              "      <td>0.626250</td>\n",
              "      <td>41.000000</td>\n",
              "      <td>1.000000</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>max</th>\n",
              "      <td>17.000000</td>\n",
              "      <td>199.000000</td>\n",
              "      <td>122.000000</td>\n",
              "      <td>99.000000</td>\n",
              "      <td>846.000000</td>\n",
              "      <td>67.100000</td>\n",
              "      <td>2.420000</td>\n",
              "      <td>81.000000</td>\n",
              "      <td>1.000000</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "      <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-afe7305f-f4cd-43f2-a8dd-c592dc3f5e5b')\"\n",
              "              title=\"Convert this dataframe to an interactive table.\"\n",
              "              style=\"display:none;\">\n",
              "        \n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n- 👋 Hi, I’m @Rithikavenkat2004
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Rithikavenkat2004/Rithikavenkat2004 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
