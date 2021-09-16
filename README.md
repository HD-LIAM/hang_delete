# hang_delete
# 2_1. 일부데이터 제외 (!= 사용)
trees = trees[trees['자치구'] != '서울시']
trees = trees[trees['자치구'] != '공원녹지사업소']
trees = trees[trees['자치구'] != '시설관리공단']
trees.head()
# head는 5개가지만 불러온다 = 표 보기 깔끔하게 하기위해서


# 2_2. isin사용한 경우
# 자치구 와 이팝나무만 별도로 데이터 프레임으로 불러옴 
pd.concat([trees['자치구'], trees['이팝나무']], axis=1)

trees2 = trees['이팝나무'][~trees['자치구'].isin(['서울시','공원녹지사업소','시설관리공단'])]

# 3_2 
trees2 = pd.to_numeric(trees2.str.replace(',','')) # 정수화
trees2.head()


# 2. isin사용 
tree5 = trees['왕벚나무'][~trees['자치구'].isin(['서울시','공원녹지사업소','시설관리공단'])]
tree5 = pd.to_numeric(tree5.str.replace(',',''))

tree6 = trees['느티나무'][~trees['자치구'].isin(['서울시','공원녹지사업소','시설관리공단'])]
tree6 = pd.to_numeric(tree6.str.replace(','or' ',''))

pd.concat([tree5, tree6], axis=1)
